## What this is
This is a fresh `rasa init` project with limited data to try to get the `inform` intent to work properly.  I have a [thread on the Rasa Community Forum](https://forum.rasa.com/t/inform-acting-quirky-might-it-be-my-training-data/31127) in case you found this outside of that forum post.

## My Goal

To allow the user to change their contact information conversationally.

*Interaction 1*
**User**: My first name is Jon
**Rasa**: Thank you, I've changed your first name to Jon
**Rasa**: I now have your name as Jon None

*Interaction 2*
**User**: My last name is Wheat
**Rasa**: Thank you, I've changed your last name to Wheat
**Rasa**: I now have your name as Jon Wheat

## My Setup in this demo

In the current project, there is limited functionality.  I have 3 additional slots, and entities that are the minimum required to get the behavior I need.

For this example, the default values for `customer_first_name`, `customer_last_name` and `customer_email` are all "None" as per the RASA defaults.  In the larger project where I'm attemting to get this to work, Rasa actually has the proper contact information for a user.

## My Problem

Rasa can successfuly perform *Interaction 1* and change the first name.  It can not seem to get *Interaction 2* to work.  

It properly detects the `inform` intent, but does not pull any entities from the user's input as seen here when running `rasa shell nlu`


```
my last name is Wheat
{
  "intent": {
    "name": "inform",
    "confidence": 0.9997451901435852
  },
  "entities": [],
  "intent_ranking": [
    {
      "name": "inform",
      "confidence": 0.9997451901435852
    },
```

What makes it even more odd, is that if I type in the exact training data I used

```
- my last name is [Franklin](customer_last_name)
```

it works

```
my last name is Franklin
{
  "intent": {
    "name": "inform",
    "confidence": 0.9999760389328003
  },
  "entities": [
    {
      "entity": "customer_last_name",
      "start": 16,
      "end": 24,
      "value": "Franklin",
      "extractor": "DIETClassifier"
    }
  ],
  "intent_ranking": [
    {
      "name": "inform",
      "confidence": 0.9999760389328003
    },
```

## My Plea

I'm unsure **WHY** it works with the first name and not the last name unless I use the training data.  It's as if the entity extraction is failing.




