*   Fix date value when casting a multiparameter date hash to not convert
    from Gregorian date to Julian date.

    Before:

        Day.new({"day(1i)"=>"1", "day(2i)"=>"1", "day(3i)"=>"1"})
        => #<Day id: nil, day: "0001-01-03", created_at: nil, updated_at: nil>

    After:

        Day.new({"day(1i)"=>"1", "day(2i)"=>"1", "day(3i)"=>"1"})
        => #<Day id: nil, day: "0001-01-01", created_at: nil, updated_at: nil>

    Fixes #28521.

    *Sayan Chakraborty*

*   Fix numericality equality validation of `BigDecimal` and `Float`
    by casting to `BigDecimal` on both ends of the validation.

    *Gannon McGibbon*


## Rails 5.2.2.1 (March 11, 2019) ##

*   No changes.


## Rails 5.2.2 (December 04, 2018) ##

*   Fix numericality validator to still use value before type cast except Active Record.

    Fixes #33651, #33686.

    *Ryuta Kamizono*


## Rails 5.2.1.1 (November 27, 2018) ##

*   No changes.


## Rails 5.2.1 (August 07, 2018) ##

*   No changes.


## Rails 5.2.0 (April 09, 2018) ##

*   Do not lose all multiple `:includes` with options in serialization.

    *Mike Mangino*

*   Models using the attributes API with a proc default can now be marshalled.

    Fixes #31216.

    *Sean Griffin*

*   Fix to working before/after validation callbacks on multiple contexts.

    *Yoshiyuki Hirano*

*   Execute `ConfirmationValidator` validation when `_confirmation`'s value is `false`.

    *bogdanvlviv*

*   Allow passing a Proc or Symbol to length validator options.

    *Matt Rohrer*

*   Add method `#merge!` for `ActiveModel::Errors`.

    *Jahfer Husain*

*   Fix regression in numericality validator when comparing Decimal and Float input
    values with more scale than the schema.

    *Bradley Priest*

*   Fix methods `#keys`, `#values` in `ActiveModel::Errors`.

    Change `#keys` to only return the keys that don't have empty messages.

    Change `#values` to only return the not empty values.

    Example:

        # Before
        person = Person.new
        person.errors.keys     # => []
        person.errors.values   # => []
        person.errors.messages # => {}
        person.errors[:name]   # => []
        person.errors.messages # => {:name => []}
        person.errors.keys     # => [:name]
        person.errors.values   # => [[]]

        # After
        person = Person.new
        person.errors.keys     # => []
        person.errors.values   # => []
        person.errors.messages # => {}
        person.errors[:name]   # => []
        person.errors.messages # => {:name => []}
        person.errors.keys     # => []
        person.errors.values   # => []

    *bogdanvlviv*


Please check [5-1-stable](https://github.com/rails/rails/blob/5-1-stable/activemodel/CHANGELOG.md) for previous changes.
