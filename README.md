# iOSPT Demo Day

## Requirements

1. Fork and clone the repository
2. **Add your presentation content**
    1. Slide deck (4 required slides)
    2. Links
    3. Answer all questions 
    4. YouTube demo video (1-2 min max)
3. Polish your Github Code repository
    1. Add screenshots and an overview to your GitHub Code Repository
    2. You should make that repository the "Public Portfolio" for your project
    3. Look at [John Sundell's Splash project](https://github.com/JohnSundell/Splash) for inspiration (code, images, GIFs)
4. Create a pull request (PR) and **tag your TL and Instructor**

## Links

* Github Code: https://github.com/LambdaSchool/ios-pt2-bw4-worn-out-vici
* Github Proposal: https://github.com/LambdaSchool/ios-build-sprint-project-proposal/pull/50
* Trello/Github Project Kanban: https://github.com/LambdaSchool/ios-pt2-bw4-worn-out-vici/projects/1
* Test Flight Signup (Recommended): `<insert beta signup link here>`
* YouTube demo video (Recommended): https://youtu.be/6tHjfCU1eBE

## Hero Image

<img src="images/WornOut.png" width="1000">

## Questions (Answer indented below)

1. What was your favorite feature to implement? Why?

    Implementing a featuring using HealthKit was my favorite part for this Build Week. It was completely new to me and getting familiar with it opens up a lot of opportunities for me to build apps that can improve people's lives. It made me excited.

2. What was your #1 obstacle or bug that you fixed? How did you fix it?

    I ran into issues when I tried to implement Core Data. I couldn't remember how to implement the relationships. I fixed it by watching a lot of video tutorials and articles. 
  
3. Share a chunk of code (or file) you're proud of and explain why.

        // https://developer.apple.com/documentation/healthkit/hkobserverquery/executing_observer_queries
        let runsType = HKObjectType.workoutType()
        let predicate = HKQuery.predicateForWorkouts(with: .running)
        let query = HKObserverQuery(sampleType: runsType, predicate: predicate) { (query, completion, error) in
            if let error = error {
                print("Error getting the new workouts: \(error)")
                return
            }
            
            self.sendNotification()
                        
            // If you have subscribed for background updates you must call the completion handler here.
            completion()
        }
        store.execute(query)
        store.enableBackgroundDelivery(for: runsType, frequency: .immediate) { (success, error) in
            if success {
                print("success")
            } else if let error = error {
                print("\(error.localizedDescription)")
            }
        }

    HealthKit provides a long-running query that monitors the HealthKit store so I can easily get the most updated sample.

  
4. What is your elevator pitch? (30 second description your Grandma or a 5-year old would understand)

    An app that helps runners track the mileage of their running shoes.
  
5. What is your #1 feature?

    Automatically tracks mileage based on your HealthKit runs.
  
6. What are you future goals?

    - Adding shoe pictures
    - User profiles
    - Shoe statistics
    - Smarter notifications

## Required Slides (Add your Keynote to your PR)

1. App Name / Team Slide
2. Elevator Pitch
3. Your #1 Feature (Customer facing — what can I do with your app?)
4. Future Goals

## Slide Requirements

1. 50 pt font minimum
2. Be concise — don't write sentences/paragraphs (put these in your slide notes for speaking)
3. 3-6 bullets maximum per slide
4. Do the squint test (can you read the text if you squint, if so, make the font bigger)
6. Images are always welcome
7. Do the Grandma Test (Would your Grandma understand you?)

### Optional Slides

1. Blooper: What's a funny bug or blooper? (screenshots/GIFs please)
2. Revenue Model: If the app was your sole source of income, how would you monetize it?

## Presentation Format

**7 minutes/team**

* 4 minute presentation (5 minute hard cap)
* 3 minutes of questions

We have ~12 teams presenting today — please practice your presentation with a timer (as a team), and make sure you fit within the time limit.

Plan on having one person present the slides and live demo. Please practice your presentation in front of a mirror or with your team 2-5 times. Have the app running and visible (Simulator or QuickTime) so you can quickly transition between slides and live demo.

* App Name / Team Slide (30 seconds)
* Elevator Pitch Slide (30 seconds)
* Your #1 Feature (30 seconds)
* Live Demo (2 minutes)
* Future Goals (30 seconds)
* Questions (3 minutes)
