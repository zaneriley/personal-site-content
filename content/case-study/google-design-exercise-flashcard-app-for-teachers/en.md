---
title: "Google's design exercise: A flashcard app for teachers"
url: "googles-design-exercise-flashcard-app-for-teachers"
company: "Google"
role: "Design Candidate"
timeline: "Dec 2017"
read_time: 9
platforms: ["android", "voice_assistant"]
sort_order: 6
introduction: "TBD"
is_draft: false
---

At the beginning of each new semester or school year, teachers are faced with the challenge of remembering names for a large number of new students. Design an experience to help an educator match faces to names, with the goal of shortening the time needed to reach complete un-aided accuracy. Provide a high-fidelity mock for at least one step of this experience.

Time Spent: 16 hours

## Research

To begin a project, I spend a lot of time collecting information and jotting down questions as they come–feature ideas, research topics, assumptions, and possible technical constraints to consider. I spoke to four teachers for this exercise. Also, I had been using spaced repetition software to learn Chinese for 2 hours a day for the last four weeks.

## Framing the problem

Before we can solve anything, we need to understand the core problem. We want to make it easier for teachers to remember their students’ names. But why is that important? If we know the motivation–why teachers want to accomplish it–we can measure our success by checking if we helped teachers achieve the outcome they wanted. I spoke to four teachers to clarify the problem and better understand their motives.
Teachers interviewed for this exercise
|                     | Austin                  | Sarah                        | Valerie                      | James                          |
|---------------------|-------------------------|------------------------------|------------------------------|-------------------------------|
| **Years Experience**| 1                       | 3                            | 16                           | 9                             |
| **Institution**     | Primary                 | Primary                      | Secondary                    | University                    |
| **# of Students**   | 24                      | 31                           | 86                           | 312                           |
| **Location**        | Bellingham, WA          | New York City, NY            | Benton, MO                   | Tallahassee, Florida          |
| **Context**         | First full-time teaching position | Co-teaches in a charter school | Teaches in a reorganized district | Teaches in large lecture formats |

It was clear that teachers were motivated to know about their students to facilitate better learning outcomes and a collaborative classroom.

    “Connecting with students makes them want to learn.”

    “It’s about looking out for the welfare of the student.”

    “Building trust and a relationship with the students in turn helps prevent behavioral issues.”

Teachers were highly motivated to learn their students’ names so that they felt more comfortable and engaged in learning. But what’s in a name? It is more complicated than simply memorizing a written classroom roster. I learned from my research:

* Pronouncing names correctly is just as important, yet can be difficult. Having students repeat their name multiple times feels awkward, and can distance the student.
* Students occasionally have a nickname they prefer, but isn’t documented. Schools don’t often track this secondary information, so it’s up to the teacher.
* No school from my group kept up-to-date photos of the students. In primary school, this is a bigger problem as students can look quite different year to year.

Most teachers developed their own individual methods to learn about their students. Some had students announce their names when answering questions. Others created name plates for their desks. Both primary school teachers in my “user group” had assigned seats.

These methods are organic versions of spaced repetition, a learning method focused on reviewing information in gradually increasing amounts of time. It’s extremely popular with students learning foreign languages, medicine and law. If you need to memorize specific information–like a name–as efficiently as possible, spaced repetition is a great fit.
Studying material is unique to the teacher.

Unlike language learning where you can download thousands of high quality flashcard decks, the information teachers need to study is completely unique to them. Getting the materials together takes time, and the more students a teacher has, the more effort is necessary to actually start studying.
The number of students impact a teacher’s intent to learn.

There are two ways the number of students can affect a teacher’s drive to learn.

    If the number of students per class becomes too big, like in a lecture setting, there’s less expectation to learn names as many students won’t interact with the teacher directly .
    If the number of students per class is small, but a teacher has many classes, the large number of students lengthens the time it takes to reach “unaided accuracy.”

Requiring fingerprint to keep student information safe.
Privacy for students is paramount.

While not directly tied to aiding the teacher’s goal, it’s critical we protect student and teacher privacy. It won’t be enough to simply require a Google account. We’ll likely want to require authentication to view the app.
Reframing the problem and solution

Having a better understanding of the problem, I made a vision statement to stay focused on the outcome teacher’s want to achieve:

Create better relationships between teachers and students.

How?

    Make it easy to start and study often.
    Provide multiple methods of studying to learn about students.
    Encourage teachers by visualizing their progress.

Measuring Success

    Recall time for a single name is less than 1 second. Recalling someone’s name for use in conversation is essentially learning a word in a new language. When speaking, the word has to be recalled almost instantly to sound conversational.
    100% of names have recall time lower than 1 second.

Out of scope

    Teachers with a large number of students per class. Even though teachers in lecture settings often have an assistant to split the class up, there’s less expectation around learning everyone’s names. Since it’s less of a problem for them, and designing experiences for 100+ students per class is different than 30, I decided to focus on teachers with smaller class sizes.

Solving the problem

I had a lot of ideas based on the research I gathered, and now having a vision statement, I could narrow down and prioritize the features.

To allow teachers the ability to study at any time, I opted for a mobile app. Much of the studying is done away from desks–on the train, while cooking dinner, or during down time–so it made sense to make the app available in those contexts.

To explore how a teacher might use this in their day-to-day, I needed to sketch out the process. It helps surface questions I’ve yet to answer which then feedback into the research process.
Focus on studying, not on making studying materials.

If it isn’t easy to start, only ambitious individuals with large amounts time and resources can tackle a new habit. Removing some of the work to get started frees up teachers to focus on studying, not on making studying materials.

If I was prototyping this, I would create the studying materials for the teachers manually so we could focus on validating the idea that our product helps teachers improve their relationship with students. It wouldn’t make sense to spend the resources finding a way to build flashcards, when what we want is to build a way for teachers to remember their students’ names.

Originally, I thought of features to get rid of manually creating flashcards all together. Most involved integrating with existing teaching tools. I assumed it was likely the school maintained the student information we need, and indeed some did, but after my user interviews, it became apparent student information and teachers’ tools varied wildly between schools. Without having more information of a teacher’s technology constraints, I decided to avoid building anything around integrations. Luckily, I don’t think we need to.
Google Cloud Vision API can detect multiple faces in a single photo.

Google Cloud Vision API allows us to recognize faces and text, which we can likely use to create the flashcards. For a photo with multiple faces, we could generate as many flashcards respectively. This helps avoid a lot of frustration in getting set up.

For pronunciation of names, I originally turned to Google Translation API. However it doesn’t seem to support text-to-speech. Thankfully, both Android and iOS support text-to-speech out of the box, so having a baseline audio pronunciation there is a good start as well.

With those constraints in mind, this is what the onboarding could look like:
Tap to expand. Create an account, set up fingerprint login, and then add your first class.

Users can join or sign in, turn on fingerprint login, and then set up their first class relatively painlessly. Ideally, they could complete their first day’s study in the same session.
Use space repetition to learn names, not memorize flashcards.

A lot has been written about the effectiveness of the spaced repetition software (SRS), so I won’t go into much detail there. However, one thing I’ve learned from studying Chinese through SRS is that it’s easy to find yourself memorizing the flashcard, and not the information in the flashcard.

This is often because you end up seeing the information presented in the same way again and again. You may know the correct answer to a flashcard is Option C, but only because you’ve seen the exact question and answer multiple times, not because you understand why the answer is Option C. You memorized the flashcard, not the information.

Keeping your brain from pattern matching like this can be tricky. The first step is to break the question and answer into different formats so you’re less likely to see the same flashcard structure. In the below user flow, I’ve created three types of questions. Recognizing a face, recognizing a name, and recalling a name.
Tap to expand. This flow shows how a teacher could learn names through multiple question formats.

But because of the amount of times you’ll need to view a flashcard to recall it in less than a second, you’re bound to see the same combinations multiple times. One method to avoid this is having the question and answers dynamically populate. This is pretty unusual, but it works well for us because faces and names match only once. Combined with Google Cloud Vision API, we could dynamically populate the questions and answers in interesting ways. For instance, we could change the difficulty by showing similar or dissimilar faces:
Can anyone actually tell Chad Smith and Will Ferrell apart?

Another common way to assist memory is using mnemonic devices. Some techniques have you construct elaborate acronyms (e.g. ROY G BIV for the colors of the rainbow), but I felt this introduced too many new techniques at once.

Instead, a teacher can add information about the student to not only serve as a recall device, but allow them to know that student even better. It’s acting as a mnemonic device, it just doesn’t need to be introduced as that. This is an easy win against our vision statement.

The app can serve as a reference guide as well. When viewing a class roster, teachers can see at a glance a student’s photo, name and information.
The class roster acts like a reference guide, allowing a teacher to see all the students at a glance.
Help teachers visualize their progress and goals.

A tough part about starting a new habit is estimating how much time and effort it actually takes to adopt it. Throughout the app, I tried to instill confidence by helping teachers plan their study, and also reaffirm why they were doing this in the first place.
Encouraging teachers by helping them plan their schedule and remind them of where they’re trying to get to.
Looking to the future

If we successfully validated this product, I think there are two areas worth looking at expanding. One is to continue reducing the friction to get started, ideally removing the need for manual flashcards. I think one way to do that is to integrate heavily with G Suite for Education, especially Google Forms.

The second area for improvement is continuing to add different teaching methods to the flashcards. Often times, finding time to study is difficult when it competes with chores or errands. But why not do them at the same time? Jeopardy is Amazon Alexa’s top skill for good reason, it’s an enjoyable way to kill time while doing the dishes or cleaning the house.