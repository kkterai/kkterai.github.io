---
layout: post
title:  Rails: Active Record Validations
date:   2016-11-18 15:47:37 -0500
---


Working through the Flatiron BnB lab in Learn.co’s Rails section has been a great challenge. In the throes of this, I want to share some lessons learned about Active Record Validations in under a five minute read for you, another committed Learner.

First, why validate? In Google, various searches around “unvalidated data” , “database”, and “web application” resulted in a common result: unvalidated input is one of the most — if not the most — critical areas of Web Application security vulnerability. If developers allow input into databases without validating first, they put those databases at risk by leaving applications open to attack via SQL injection.

If you are now convinced to get on the Validation Train, you are probably wondering, “How do I do it?” Validations essentially ensure that only valid data is saved into a database. From the perspective of Rails, Model-level validations are the best choice in most circumstances and will be the focus here.

**The Object Life Cycle: The “When” of Active Record(AR) Validations**

Rails runs validations before saving an AR object to the database. There are two key points in time that have convenient validation-triggering methods:
* Between when a new AR object is created and when a SQL `INSERT` operation is sent to the database (Methods: `CREATE`,`CREATE!` ,`SAVE`,`SAVE!`)
* Between when an existing record is edited in an edit form and when a SQL `UPDATE` operation is sent to the database (Methods: `UPDATE`, `UPDATE!`)

If errors are produced at any of these points, the object will not be saved to the database. Note that you can also run validations on your own. `VALID?` triggers your validations and will return true if no errors are found in the object, and false otherwise.

After running validations, an object’s collection of errors can be accessed by calling the `errors.messages` instance method. If this collection is empty, then the object is considered valid.

**Active Record: Pre-Defined Validation Helpers**

Good for minimizing lines of code, each helper accepts an arbitrary number of attribute names. With a single line of code you can add the same kind of validation to several attributes!

Here is a list of the available helpers from the [Rails Guides](http://guides.rubyonrails.org/active_record_validations.html#validation-helpers):

* [`acceptance:`](http://guides.rubyonrails.org/active_record_validations.html#acceptance) validates that a checkbox on the user interface was checked when a form was submitted.
* [`validates_associated:`](http://guides.rubyonrails.org/active_record_validations.html#validates-associated) When you try to save your object, valid? will be called upon each one of the associated objects.
* [`confirmation:`](http://guides.rubyonrails.org/active_record_validations.html#confirmation) Two text fields must receive exactly the same content (e.g. email confirmation). Must be used along with a presence check and case sensitivity defaults to true.
* [`exclusion:`](http://guides.rubyonrails.org/active_record_validations.html#exclusion) Validates that specific attribute values are not included.
* [`format:`](http://guides.rubyonrails.org/active_record_validations.html#format) Validates the attributes' values by testing whether they match a given regular expression.
* [`inclusion:`](http://guides.rubyonrails.org/active_record_validations.html#inclusion) Validates that specified attributes’ values are included.
* [`length:`](http://guides.rubyonrails.org/active_record_validations.html#length) Validates the length of attribute values. Constraint options include `:minimum`, `:maximum`,`:in`(or `:within`), and `:is`.
* [`numericality:`](http://guides.rubyonrails.org/active_record_validations.html#numericality) Validates that your attributes have only numeric values. Default is to convert a value to a Float; set `:only_integer` to true to allow only integral numbers. There are additional constraint options available, such as `:greater than`. See documentation for details.
* [`presence:`](http://guides.rubyonrails.org/active_record_validations.html#presence) Can not only validate that specified attributes are not empty, but can also validate the presence of an association. In addition, you can also validate presence of associated records by using the `:inverse_of` option for the association. See documentation for validating presence of a boolean field.
* [`absence:`](http://guides.rubyonrails.org/active_record_validations.html#absence) Validates that the specified attributes are absent.
* [`uniqueness:`](http://guides.rubyonrails.org/active_record_validations.html#uniqueness) Validates that the attribute’s value is unique right before the object gets saved.
* [`validates_with:`](http://guides.rubyonrails.org/active_record_validations.html#validates-with) This helper passes the record to a separate class for validation.
* [`validates_each:`](http://guides.rubyonrails.org/active_record_validations.html#validates-each) This helper validates attributes against a block.

All of them accept the `:on` and `:message` options; `:on` defines when the validation should be run and `:message` defines what message should be added to the errors collection if it fails. You can find more on these options’ use [here](http://guides.rubyonrails.org/active_record_validations.html#common-validation-options).


---

**References and further reading**

[Hacker Lexicon: SQL Injections, an Everyday Hacker's Favorite Attack](https://www.wired.com/2016/05/hacker-lexicon-sql-injections-everyday-hackers-favorite-attack/)

[Active Record Validations - Ruby on Rails Guides](http://guides.rubyonrails.org/active_record_validations.html)

[Rubular: a Ruby regular expression editor and tester](http://rubular.com/)

