# python-checkpoint-config
Python Scripts to interact with the Checkpoint R80 API

The idea here is develope a set of scripts to provide functions for a user to be able to configure Firewall Rules and other parts of Checkpoints security policies.

The Checkpoint API in R80 still has a number of items you can't manipulate yet (Cluster Objects, Users...).
It's early days, but there's still plenty to work with.

Currently the plan is as follows:

A API library:
 - Called by Function Library
 - Performs final sanitization of input and prepares for the API call
 - Makes the API call
 - Prepares result output and status and returns

A Function library:
 - Called by users script
 - Sanitization of user input
 - Calling API functions
 - Handling output and errors

The plan is initially for the functions will be based around:
 - Adding New Access/NAT Rules, creating the required objects where required
 - Creating a New Access policy with a consitant template
Configuration will be fed from a YAML file, which will describe the rules/NATs and the objects they use

Future plans would be to use YAML files to describe the entire configuration of a rulebase & objects on the firewall
Any desired changes to the policy will be configured here and the scripts will work out the difference between the Live configuration and the desired configuration and then action the required changes to make it so.

This may work nicely for smaller policies and objects, but for larger more complex policies it could become problematic and require additional time/processing/memory and increasing number of API calls.
Who knows, maybe it'll all work out!
