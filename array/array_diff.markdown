# array_diff

In Ruby, many operators are implemented as methods, and you can even redefine them.

{{code:php
    $animals1 = array('cat', 'dog', 'bat', 'rat');
    $animals2 = array('bat', 'rat');

    $result = array_diff($animals1, $animals2);
    var_export($result);
    // => array(0 => 'cat', 1 => 'dog')
}}

{{code:ruby
    ['cat', 'dog', 'bat', 'rat'] - ['bat', 'rat']
    # => ["cat", "dog"]
}}

That is equivalent to calling:

{{code:ruby
    ['cat', 'dog', 'bat', 'rat'].-(['bat', 'rat'])
    # => ["cat", "dog"]
}}

If you don't quite agree with Ruby on how exclusions should be handled, Ruby lets you have it your way:

{{code:ruby
	def Array
		def - other
			self.each_with_index do |item, i|
				self[i] += '-blacklisted' if other.include? item
			end
		end
	end

    ['cat', 'dog', 'bat', 'rat'] - ['bat', 'rat']
    # => ["cat", "dog", "bat-blacklisted", "rat-blacklisted"]
}}

{{related:
    array/array_diff_assoc    
    array/array_intersect     
    array/array_intersect_assoc
}}
