# OMUS Parameterized Algorithm Notation
## OPAN
OPAN is a notation for describing parameterized algorithms &mdash; that is, algorithms wherein the procedure may depend on aspects of the context in which the algorithm is being executed. OPAN algorithms, in addition to taking in parameters can return values, allowing the result of one algorithm to be a parameter of another.   
In OPAN, algorithms are described mainly as a series of actions, with added components to support nested algorithms and variables. In addition to these components, algorithms can specify external actions and names. External actions are processes which are not described in the algorithm, and the executer is expected to already understand how to do. External names, similarly, are variables the value of which the executer is expected to already know (eg. numbers). Despite obvious similarity to functions (or procedures) in computer programming languages, these external objects allow OPAN to be used to describe any kind of algorithm, including those used by computers, but also those used by people.

## Example
This algorithm describes a process to approximate the square root of a number 'x'. It requires external actions for math, such as addition and subtraction, a conditional action 'if', a random number generator, and an identity action, which would simply return its input.
```
<sqrt x :>
	@ea id abs + - / < if rand
	@en epsilon 1 2
	g : rand 1 x
	<iter>
		newG : / (+ g (/ x g)) 2
		dif : abs (- g newG)
		g : id newG
		if (< dif epsilon) iter
	iter
	id g :
```
## Rules
### Structures
- Special character: \<space>|\<tab>|\<newline>|:|(|)|'<'|'>'
- Ordinary character: \<character that is not a special character>
- Name: \<series of ordinary characters>
- Action: \<action item> [\<series of space-separated action items>] [:]
- Action Item: \<name>|\<embedded action>
- Embedded Action: (\<action without ' :' at end>)
- Definition: \<name> : \<action>
- Directive: @'ea'|'en'\<series of space-separated names>
- Algorithm Head: '<'\<name>[\<series of space-separated names>][ :]'>'
- Line: [\<series of tabs>]\<algorithm>|\<action>|\<definition>|\<directive>\<newline>
- Algorithm: \<algorithm head>\<newline>\<series of lines>

Lines begin with one more tab than directly precede the algorithm they are a part of.
### Algorithm Construction
An algorithm's name is the first name in its head.  
An algorithm's inputs are the names in the optional series of names in its head. If this series is not provided, the algorithm has no inputs.  
If an algorithm's head contains ' :', that algorithm has a return value.  
Lines containing directives appear as the first line in an algorithm, or directly after a line containing a directive.  
An algorithm can only contain one directive beginning with each possible start (eg. 'ea'), not including directives within other algorithms.
### Action Construction
An action's name is the first action item in it.  
An action's set of inputs is the optional series of action items.  
### Definition Construction
A definition's mapping must value a name at least once.  
If a definition's mapping values a name exactly once, that name cannot appear in the action interpreted soonest after the definition, unless the interpretation of that action requires interpreting another action before interpreting the name.
### Scoping
Each algorithm has a scope.  
A scope's parent is the scope of the algorithm that contains the child scope's algorithm.
### Name Interpretation
The value of a name is the value that name was most recently mapped to within an accessible scope.  
A scope is accessible if it is the scope of the algorithm a line is part of, or somewhere above that scope on its parent tree.  
An algorithm maps its name to itself, within its scope's parent.  
A definition maps its name to the return value of its action.  
A definition's mapping happens within the nearest accessible scope unless there is a different accessible scope in which a different definition has already mapped the definition's name to something. In that case, the definition's mapping happens within that other accessible scope.  
An 'en' directive maps each name in its series of names to an unknown value, within the nearest accessible scope.  
An 'ea' directive maps each name in its series of names to an unknown action, within the nearest accessible scope.
###  Action Interpretation
Embedded actions are evaluated like actions, ignoring the parentheses.  
The action's name is interpreted first, then each of the action's inputs in the listed order.  
The value of an action's name is either an algorithm or an unknown action.  
If the value of the action's name is an algorithm, the algorithm is interpreted, with its parameters being the values of the action's inputs. In this case, the action's return value is that of the algorithm.  
### Algorithm Interpretation
First, an algorithm maps each of its inputs to the corresponding parameter in its parameters, within its scope.  
An algorithm interprets each of its lines that do not contain algorithms or directives in order.  
An algorithm returns the return value of the last action it interprets that ends with ':'.  
If an algorithm never interprets an action ending with ':', that algorithm does not return anything.
