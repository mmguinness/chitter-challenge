Chitter Challenge
=================

How to use:
-------
* Clone this repo.
* Run the command 'bundle' in the project directory to ensure you have all the gems.
* Run tests with RSpec.
* Run tests with Rubocop.
* Run ruby app.rb in terminal to view in localhost port.

Planning:
-------
![Database Model](/public/CRC_Card_diagram_01.png)

* Setup environment - Sinatra and Capybara introduced.
* https://github.com/makersacademy/course/blob/main/pills/ruby_web_project_setup_list.md

* First feature - post a peep
![Views](/public/Post_a_peep.png)

#### Setting Up Database

- Connect to `psql`
- Create the database using the `psql` command `CREATE DATABASE chitter;`
- Connect to the database using the `pqsl` command `\c chitter;`
- Run the query saved in the file `01_create_peep_table.sql`
- Create the test database using the `psql` command `CREATE DATABASE chitter_test;`
- Connect to the database using the `pqsl` command `\c chitter_test;`
- Run the query saved in the file `01_create_peep_table.sql`



* Setup environment - pg gem introduced.
- To incorporate a database into Chitter I used the `PG` gem and `SQL` queries to store peeps, and display on Chitter.

![Domain](/public/request_response_diagram.png)

- Setup peep content and time together as it is same form process.
- Peeps rearranged to show in reverse order.
- Web helper added to reduce setup for tests.
- Time format not updated. I tried to change this in the html rather than the database but could not get `HTML <time> datetime Attribute` to work for me.

- I ran out of time to complete more of the challenge. Next I would tackle how to sign up for chitter and create a User class to store the information for user signing up. This name & username could then be displayed on the peeps. 

- HTML updated using Bulma template to format text size and location on page.

![View index.erb](/public/Homepage_view.png)

![View peeps.erb](/public/Peeps_view.png)

-------



Challenge:
-------

We are going to write a small Twitter clone that will allow the users to post messages to a public stream.

Features:
-------

```
STRAIGHT UP

As a Maker
So that I can let people know what I am doing  
I want to post a message (peep) to chitter

As a maker
So that I can see what others are saying  
I want to see all peeps in reverse chronological order

As a Maker
So that I can better appreciate the context of a peep
I want to see the time at which it was made

As a Maker
So that I can post messages on Chitter as me
I want to sign up for Chitter

HARDER

As a Maker
So that only I can post messages on Chitter as me
I want to log in to Chitter

As a Maker
So that I can avoid others posting messages on Chitter as me
I want to log out of Chitter

ADVANCED

As a Maker
So that I can stay constantly tapped in to the shouty box of Chitter
I want to receive an email if I am tagged in a Peep
```

Technical Approach:
-----

In this unit, you integrated a database into Bookmark Manager using the `PG` gem and `SQL` queries. You can continue to use this approach when building Chitter Challenge.

If you'd like more technical challenge now, try using an [Object Relational Mapper](https://en.wikipedia.org/wiki/Object-relational_mapping) as the database interface.

Some useful resources:
**Ruby Object Mapper**
- [ROM](https://rom-rb.org/)

**ActiveRecord**
- [ActiveRecord ORM](https://guides.rubyonrails.org/active_record_basics.html)
- [Sinatra & ActiveRecord setup](https://learn.co/lessons/sinatra-activerecord-setup)

Notes on functionality:
------

* You don't have to be logged in to see the peeps.
* Makers sign up to chitter with their email, password, name and a username (e.g. samm@makersacademy.com, password123, Sam Morgan, sjmog).
* The username and email are unique.
* Peeps (posts to chitter) have the name of the maker and their user handle.
* Your README should indicate the technologies used, and give instructions on how to install and run the tests.

Bonus:
-----

If you have time you can implement the following:

* In order to start a conversation as a maker I want to reply to a peep from another maker.

And/Or:

* Work on the CSS to make it look good.

Good luck and let the chitter begin!

Code Review
-----------

In code review we'll be hoping to see:

* All tests passing
* High [Test coverage](https://github.com/makersacademy/course/blob/main/pills/test_coverage.md) (>95% is good)
* The code is elegant: every class has a clear responsibility, methods are short etc.

Reviewers will potentially be using this [code review rubric](docs/review.md).  Referring to this rubric in advance may make the challenge somewhat easier.  You should be the judge of how much challenge you want at this moment.

Automated Tests:
-----

Opening a pull request against this repository will will trigger Travis CI to perform a build of your application and run your full suite of RSpec tests. If any of your tests rely on a connection with your database - and they should - this is likely to cause a problem. The build of your application created by has no connection to the local database you will have created on your machine, so when your tests try to interact with it they'll be unable to do so and will fail.

If you want a green tick against your pull request you'll need to configure Travis' build process by adding the necessary steps for creating your database to the `.travis.yml` file.

- [Travis Basics](https://docs.travis-ci.com/user/tutorial/)
- [Travis - Setting up Databases](https://docs.travis-ci.com/user/database-setup/)

Notes on test coverage
----------------------

Please ensure you have the following **AT THE TOP** of your spec_helper.rb in order to have test coverage stats generated
on your pull request:

```ruby
require 'simplecov'
require 'simplecov-console'

SimpleCov.formatter = SimpleCov::Formatter::MultiFormatter.new([
  SimpleCov::Formatter::Console,
  # Want a nice code coverage website? Uncomment this next line!
  # SimpleCov::Formatter::HTMLFormatter
])
SimpleCov.start
```

You can see your test coverage when you run your tests. If you want this in a graphical form, uncomment the `HTMLFormatter` line and see what happens!
