# Rails cheatsheet

## Active Record associations
  * belongs_to
      * one to one, declaring model belongs to one instance of the other model. *FK in declaring model*  Ex. Order(customer_id_fk) belongs_to Customer 
  * has_one
      * one to one, each instance of a model contains or possesses one inst. of another model. *FK in model called by the helper* Ex. Supplier has_one account(supplier_id_fk)
  * has_many
      * one to many, fk in model called by helper Ex. Customer has_many Orders(customer_id_fk)
  * has_many :through
      * many to many between two models through an third model. Ex. Physicians[id|name] / Patients[id|name] through Appointments[id|patient_id|physician_id|appointment_date]
      phy has_many appointments, has_many pat through appointments; Appointments belongs to pat, belongs to phy, Pat has_many appointments, has_many phy through appointments
  * has_one :through
      * one to one between two models through a third one. Ex. Supplier[supplier_id|name] Accounts[id|supplier_id|account_number] Account_histories[id|account_id|credit_rating]
      sup has_one account, has_one account_history through account, Account belongs to sup, has_one account_history, AccountHistory belongs_to account
  * has_and_belongs_to_many
      * many to many, without third model involved

### When to use guide

  * belongs_to and has_one
    One to one associations, you have to decide where you want to have the FK
  * has_many :through and has_and_belongs_to_many
    The simplest rule of thumb is that you should set up a has_many :through relationship if you need to work with the relationship model as an independent entity. If you don't need to do anything with the      relationship model, it may be simpler to set up a has_and_belongs_to_many relationship (though you'll need to remember to create the joining table in the database). You should use has_many :through if yo    u need validations, callbacks, or extra attributes on the join model.

### Polymorphic
  
  * You have a model that can assume different "shapes", like for examples a Picture model: It could store either a product picture or a user picture.
    picture belongs_to imageable, polymorphic true; 
    employee has_many pictures, as imageable;
    product has_many pictures, as imageable;

### Self Joins

  * To track self-referring relations in a model, like tracking subordinates between employees:
    Employee has_many subordinates, class_name: "Employee", foreign_key: "manager_id"
    Employee belongs_to :manager, class_name: "Employee"

