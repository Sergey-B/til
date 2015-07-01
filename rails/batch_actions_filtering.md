# Apply filtering to batch_action_collection

When performing a batch action on a filtered set of records, batch_action_collection returns all records.

```ruby
# app/admin/photos.rb

batch_action :pending do |selection|
   ActiveRecord::Base.transaction do
     Photo.find(selection).each(&:pending!)
   end

   redirect_to :back, notice: 'Успешно отправлены на модерацию'
 end
```
