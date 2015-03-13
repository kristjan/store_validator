## Supported validators
### presence

** Purpose: ** Ensure that a value is not nil or blank.

** Accepted values: **
  - true
  - false

** Example: **
```ruby
validate_store_accessor :foo, presence: true
```
<hr/>
### allow_blank

** Purpose: ** Allow a value to be nil or blank.

** Accepted values: **
  - true
  - false

** Example: **
```ruby
validate_store_accessor :foo, allow_blank: false
```
<hr/>
### allow_nil

** Purpose: ** Allow a value to be nil.

** Accepted values: **
  - true
  - false

** Example: **
```ruby
validate_store_accessor :foo, allow_nil: true
```
<hr/>
### exclusion

** Purpose: ** Ensure that a value is not in a specified list.

** Accepted modifiers: **
  - array of values to exclude

** Example: **
```ruby
validate_store_accessor :foo, exclusion: { in: ['bar', 'baz'] }
```
<hr/>
### inclusion

** Purpose: ** Ensure that a value is in a specified list.

** Accepted modifiers: **
  - array of values to exclude

** Example: **
```ruby
validate_store_accessor :foo, inclusion: { in: ['bar', 'baz'] }
```
<hr/>
### length

** Purpose: ** Ensure that a value's length matches a minimum and maximum or an exact integer.

** Accepted modifiers: **
  - `:min` and `:max`
  - range of integers
  - exact length integer

** Examples: **
```ruby
# :min and :max
validate_store_accessor :foo, length: { min: 15, max: 30 }

# range of integers
validate_store_accessor :foo, length: (2..9)

# exact length integer
validate_store_accessor :foo, length: 15
```
<hr/>
### numericality

** Purpose: ** Ensure that a value matches various comparisons.

** Accepted modifiers: **
  - greater_than
  - greater_than_or_equal_to
  - equal_to
  - less_than
  - less_than_or_equal_to
  - odd
  - even
  - only_integer

** Examples: **
```ruby
validate_store_accessor :foo, numericality: { greater_than: 10 }

validate_store_accessor :foo, numericality: { greater_than_or_equal_to: 5 }

validate_store_accessor :foo, numericality: { equal_to: 1 }

validate_store_accessor :foo, numericality: { less_than: 20 }

validate_store_accessor :foo, numericality: { less_than_or_equal_to: 10 }

validate_store_accessor :foo, numericality: { odd: true }

validate_store_accessor :foo, numericality: { even: true }

validate_store_accessor :foo, numericality: { only_integer: true }
```
<hr/>
### type

** Purpose: ** Ensure that a value is of a specific type.

** Accepted values: **
  - `:array`
  - `:boolean`
  - `:float`
  - `:float`
  - `:integer`
  - `:hash`
  - `:string`

** Example: **
```ruby
validate_store_accessor :foo, type: :boolean
```
