# Reset primary keys for all models

```ruby
ActiveRecord::Base.connection.tables.each do |table_name|
  ActiveRecord::Base.connection.reset_pk_sequence!(table_name)
end
```