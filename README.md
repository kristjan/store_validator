## Store Validator

### ActiveRecord validations on dynamic columns

Using [ActiveRecord::Store](http://api.rubyonrails.org/classes/ActiveRecord/Store.html) enables flexible schema by using postgres' hstore or json type columns.

`ActiveRecord::Store` implementation is sometimes too flexible. When data integrity is important, validations are a good way to make sure your data is clean and consistent.

This gem allows validations on specific attributes within those flexible columns.

Store Validator can be used like any other active record validator

```ruby
class Foo < ActiveRecord::Base
  store_accessor :settings, :role

  validate_store_accessor :settings, presence: true

  validate_store_accessor :role, in: ['User', 'Admin', 'SuperAdmin']
end
```

Additionally, Store Validator can check types of values in columns. Since `store_accessor` does not use statically typed columns, database adapters like the pg gem do not know how to cast incoming data to proper types.

```ruby
class Foo < ActiveRecord::Base
  store_accessor :settings, :role, :active

  validate_store_accessor :settings, type: :array

  validate_store_accessor :role, type: :string

  validate_store_accessor :active, type: :boolean
end
```

Multiple validations can be asserted on a field in one statement.

```ruby
class Foo < ActiveRecord::Base
  store_accessor :role

  validate_store_accessor :role,
                          type: :string,
                          in: ['User', 'Admin', 'SuperAdmin']
end

```

For a full list of validations applicable to store_accessor columns refer to the [validations page.](validations.md)
