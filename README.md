# Strava Lite
## Project Information
- GitHub Repository: https://github.com/DevGritHub/Flask-Project.git
- Name: Devesh Sharma
- Email: dsharma11@stevens.edu
- CWID: 20036824
## Project Description
Strava Lite is a basic server application to help users track their runs. It allows users to register, view their profile, list all users, add workouts, list their workouts, and delete their account. Additionally, it includes social features where users can follow other users and view their friends' workouts.
## Features
- User account creation and management (covers RegisterUser, GetUser, RemoveUser, ListUsers).
- Recording and listing workouts (covers AddWorkout, ListWorkouts).
- Social following to view friends' workouts (covers FollowFriend, ShowFriendWorkouts).
## How to Run
1) Set up a Python environment
2) Install dependencies: pip install -r requirements.txt
3) Run the server: python app.py
4) Server runs on http://127.0.0.1:5000, which matches the BASE URL in my test.py file
5) Run the Test Script: python test.py
## Bugs and Issues Faced
1) Issue: When returning the list of followed users, UUIDs in the set weren't properly serializing to JSON.<Br>Solution: Added explicit string conversion when returning the list: 
return {"following": list(map(str, users[user_id]["following"]))}, 200

2) Issue: The following set wasn't being properly initialized for new users trying to follow others.<Br>Solution: Added initialization check in FollowFriend class:
if "following" not in users[user_id]: users[user_id]["following"] = set()
