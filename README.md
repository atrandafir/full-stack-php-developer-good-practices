# Introduction

Welcome to the full-stack-php-developer-good-practices wiki!

This guide provides a list of concepts, ideas and good practices common to full stack php developers and not only.

This is not about development methodologies by more about how to work properly in a way that ensures consistency and good results for your project.

# Autocompleting objects in IDE

Basically when you do the coding you can have every variable and object and property available to autocomplete and to click and go to definition, or you don't.

But I consider this is a very good practice.

To be able to write: $class->property and have all the properties autocompleted.

To be able to click on $object and go to it's definition and so on.

Depending how you're writing code and what IDE you're using, this can come out of the box, or not.

But you should make sure you implement this as a standard in your application:

Ways you can do it:

- Specifically set variable Tye inside function argumentns, example: fucntion sayHello(Person $person, string $message)
- Add /* @var Person $person */ inside view files or functions to have the same effect

# Build systems not features

When you build a feature, some time it is something small that doesn't affect the rest of the application so you can just take the Trello task and implement it.

But most of the time you're building things inside a bigger project.

So before developing that feature, make sure you try to understand how the system works.

Be an architect for a while, before doing the coding.

Sketch your ideas, double check existing code and database structure.

Only then do the coding.

# Developing a new feature

The checklist for developing a new feature on a project is the following:

1. Gather all the required information
2. Do your analysis and brainstorm
3. Draw system sketches on paper to see how things connect
4. Identify specific tasks to be done
5. Identify database changes that need to be done and generate the proper migrations
6. Implement them one by one and test that everything is working properly (with an MVP mind leaving some details for later)
7. Do some more testing before commiting (test as user, what you have built)
8. Pre-commit self-code review and identify adjustments for future iterations
9. Push to git and deploy
10. Test feature online as real user and even with real data and even in production (force yourself to deliver production-ready features)
11. Now it is the time to notify the customer by email, explaining how the feature works and how they can test it

Finally, based on customer feedback, repeat and iterate again the process until the feature is bullet proof.

# Modules development for space

Basically the idea here is simple.

But this one you learn only after building complex applications for years.

What happens is that the application grows and your controller directory ends up with 100 controllers.

That's no fun.

Solution?

Break your application into modules, example:
- Admin
- Invoicing
- Documentation
- And so on, each "part" of your application has its own place inside a directory with its own controllers, models, views, etc

This is not just about having things better organized but it is also about giving things their own place where they can develop.

Think of this as a plant. If your plant is put inside a very small pot, it won't grow.

Think of it from a creativity point of view. If you need to make a new drawing, and you have a sheet of paper that already contains lots of other drawings and only one small corner is available, you don't have enough mental space in that corner to express yourself.

# Provide easy ways to test payments

The name of this item is just an example.

The idea is the following.

Imagine you're integrating a Payment Gateway on a custom Checkout process.

And in your shop you have products with pricing as 200usd per item.

In this case if you want to test and validate that everything works in production you have two options.

Option A) 

You use your real credit card and pay 200usd for the product you need to buy in order to validate it works

Option B)

You design the system in such way, so that you can test it by paying only 1usd so you can do more tests without worrying about money.

How?

Well one smart solution could be:
- Add a field on the Users table named "Use Testig Price"
- Then in your Checkout system, if the user has that checkbox enabled, set the order amount to 1USD instead of 200USD

So this is just a concept but the main idea is:  

Whenever you feel like a feature is hard to test as a user, try to come up with smart ways to overcome that and make the process less painful.

This can benefit the user but the main benefit is that you as a developer can improve the quality of your applications by making it easier for yourself to test critical processes.

# Stay lean, keep things light

## Light development

Well I have a shitty laptop with 8GB of ram.

I'm coding mostly PHP projects with Yii framework.

It is quick and light. I just roll out some local web server and build my applications.

But, some developers use things like Docker, and I get the benefits of using it in order to build a virtual server with the exact requirements of the application.

But for me to use Docker means more RAM and more setup to be done locally just to be able to run a simple project.

My computer then works slow, I the application is loading slow, my developing experience is slow and I'll start to hate it.

## Light deployment

Most of my projects can run on a 5USD/mo VPS.

When I need to deploy my code I just SSH to the VPS, and run a script that will pull from the repo, install composer packages, and apply database migrations. It takes 5 seconds. And if I need to debug anything, is just check the logs.

Some people, setup a big infrastructure on AWS and then setup ElasticBeanstalk that for every new deployment, it needs to rebuild the whole damn project from scratch and it takes 10 minutes and it often fails and you have to lose time to see what the fuck failed and if you want to see the logs you need to do some weird shit. What the fuck people stop making your life difficult if it is not necessary.
