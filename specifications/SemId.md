# OMUS Semantic Identifiying 1.0.0
## SemId

DISCLAIMER: This specification assumes a baseline understanding of personal pronouns. If you do not have that, the aptly-named website [pronouns.org](https://pronouns.org) has some basic information. 

Many see pronouns in bios and are confused not by why they are there but by the details of the pronoun use: does he/they mean he and they equally, or is he preferred over they? 
People often use they/he, presumably to indicate a preference of they, but it's not standard, and some people get mad when they say he/they but people only use he or they and don't mix and match, while others don't care as long as you use one of them. 
To solve this confusing muddle, we present Semantic Identifying (SemId).

## Definitions
For the purposes of SemId, "pronoun" refers to an abstract category of pronoun, or the set of pronouns that are all forms of the same thing (eg. he, him, and his are all forms of the same pronoun). 
"pronoun form" will be used to refer to individual linguistic pronouns like "he" or "him". 
The entire identifier—the pronouns in bio—will be referred to as the "pronoun key".

## The Idea
A pronoun key describes the author's preferred pronouns, and the details of how much they prefer each pronoun to be used to refer to them relative to the others. 
Any pronoun that appears in the key would be okay with the author to be used, but more preferred ones should generally be used more often, or in more situations. 
Maybe the author prefers a neopronoun but is also okay with a traditional pronoun and offers that as an alternative, since some people are uncomfortable using neopronouns, for example. 
Importantly, a pronoun key should generally not include pronouns that the author does not identify with but would prefer to be used around certain people—most likely because they are not out everywhere. That should be a separate conversation.

## The Structure
#### This is the normative part  
A pronoun key is wrapped in parentheses, and immediately after the closing parenthesis is the version (or just major version number) of SemId used to write the key. 
Within the parentheses is an ordered list of sets. Each set is a series of pronoun forms separated using '/' or '+' characters (with no whitespace), and each set in the list is separated using a ',' character, with an optional space between the comma and the next item. 
No separators ('/', '+', or ',') are allowed at the end of a set or list, only between two items. 

The list is a ranking of the pronouns, with the first listed being the most preferred, and the last listed being least preferred (which is "first" and which is "last" is dependent on the writing direction of the text). 
All the pronouns within the same set are preferred equally, all at the ranking corresponding to their position in the list. 
Items in the same set separated by a '+' are still preferred equally, but also are specifically preferred to be used roughly equal amounts, while with items separated by a '/', a speaker may choose to use only one and ignore the other. 
The same set may contain some items separated by a '+' and some by a '/'. 

Each item in the set is not actually written as a pronoun, of course, but a pronoun *form*. The same pronoun form must not appear more than once anywhere in the key. 
For each pronoun that appears in the key, the nominative form of that pronoun must appear and it must be listed before any other forms, and all forms of the pronoun must be in the same set. 
Forms of the same pronoun must be separated with a '/', not a '+'. 

The pseudo-forms "any" and "all" may be used, which represent any pronoun which does not have forms listed elsewhere in the key. If both "any" and "all" appear, they must be in the same set. 
To indicate a preference for no third-person pronouns, leaving the list empty is sufficient (i.e. "```()1```"), but the pseudo-form "no pronouns" may be used instead. If this pseudo-form appears, no other forms may appear in the key.

## Examples
- Traditional, non-Semantic pronoun keys need little addition to become SemIds: "```(he/him)1```" and "```(they/them)1```" are perfectly fine makeovers of "he/him" and "they/them"
- The aforementioned "he/they" can be clarified as either "```(he/they)1```" for equal preference, "```(he,they)1```" for he being preferred over they, or "```(he+they)1```" for equal preference and preference for them being used equally
- The rather common "they/he" usually refers to "```(they,he)1```" where they is preferred over he, but could also mean "```(they/he)1```" where they are equally preferred (or even "```(they+he)1```")
- For a more complicated example, consider: "```(they,she/he,any)1```", where any pronouns may be used, but they/them pronouns are most preferred, she/her and he/him are in the middle, and everything else is less preferred
