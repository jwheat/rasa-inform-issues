## happy path
* greet
  - utter_greet
* mood_great
  - utter_happy

## sad path 1
* greet
  - utter_greet
* mood_unhappy
  - utter_cheer_up
  - utter_did_that_help
* affirm
  - utter_happy

## sad path 2
* greet
  - utter_greet
* mood_unhappy
  - utter_cheer_up
  - utter_did_that_help
* deny
  - utter_goodbye

## say goodbye
* goodbye
  - utter_goodbye

## bot challenge
* bot_challenge
  - utter_iamabot

## Profile inform change contact first name
* inform{"customer_first_name": "Freddy"}
  - utter_tell_change_first_name
  - utter_tell_new_customer_name

## Profile inform change contact last name
* inform{"customer_last_name": "Krueger"}
  - utter_tell_change_last_name
  - utter_tell_new_customer_name

## Profile inform change contact email address
* inform{"customer_email": "steven.myers@nearlyhuman.ai"}
  - utter_tell_new_customer_email
