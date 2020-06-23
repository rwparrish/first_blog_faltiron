---
layout: post
title:      "Verifying associations in Rails"
date:       2020-06-23 03:43:59 +0000
permalink:  verifying_associations_in_rails
---


As I approached my first Ruby on Rails project, I felt like I was looking up at Mt. Everest. I was trying to remember everything I learned that lead up to Rails and the feeling of overwhelming panic had set in. What if I am not learning and remembering as much as I should be!? What if I fail at this project!? Does that mean I can’t become a Ruby programmer one day? I know I am not the only software engineering student that has felt this way and I know there will be many more to face “Mt. Everest”. So, I have decided to write about a small step that I took, in the beginning, to help me get some good momentum going.

One of the great things about the cohort that I am currently in is the budding friendships that have come with the struggle. The more you reach out and ask for some help, the more you can learn. Sometimes, just overcoming the fear that others will judge you for not being the “perfect” student/coder is truly the first step. A fellow student asked me what my plan was to get the ball rolling. I had a vague idea and I think I said something about building one controller action, then the route, then the view, and repeat. He suggested a different approach which I would like to share, as I found it to be a great first step for any project build that requires complex relationships.

My relationships were as follows:
```
class Workout < ApplicationRecord
...
has_many :exercises
has_many :users, through: :exercises
...

class User < ApplicationRecord
...
has_many :workouts, through: :exercises
has_many :exercises
...

class Exercise < ApplicationRecord
...
belongs_to :workout
belongs_to :user
...
```
We will be verifying these associations. So we head into the terminal and play in the Rails console ```rails c``` to create a couple users:
```
c = User.create(name: "Stan", email: "stan@stan.com", password: "password")
```
"c" is arbitrary here and is used to call the newly created user, if we do this we can confirm that the new user has been assigned a `user_id` of 1, meaning it was successfully saved to the db. We should be able to see the attributes that were passed in as well (name, email, password). Repeat the process to create a second user which should save with a `user_id` of 2. Great! We've got our users. Now on to workouts. It's important to create the users and workouts first, given that our joins table is exercises. You can see this in the relationships provided above. 
```
c = Workout.create(name: "HIIT", notes: "No rest")
```
Very similar to our users example. This should save with a `workout_id` of 1. You can confirm this by calling `c` in the terminal. Make one more workout and then it's time to create exercises:
```
c = Exercise.create(name: "Burpee", user_id: 1, workout_id: 1)
```
Here I assigned foreign keys to the exercise object and then checked to see if it saved to the db by calling `c` in the terminal. 
```
c = Exercise.create(name: "Pushup", user_id: 2, workout_id: 1)
c = Exercise.create(name: "Situp", user_id: 1, workout_id: 2)
```
Now we can call `User.all.first.workouts` or `User.all.last.exercises` or `Workout.all.last.exercises` for example. 

I hope this helps you get started. It's important to verify these relationships are working correctly before getting too deep into your project. 

Happy coding!







