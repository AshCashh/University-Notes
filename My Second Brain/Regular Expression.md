---
Created: 2024-05-15T11:42:13+10:00
Modified: 2024-07-03T19:35:33+10:00
tags:
  - logic
---
Regular expressions are a way we can specify a [[Regular Language]] over an alphabet $\sum\limits$. Regular expressions over an alphabet $\sum\limits$ are strings over $\sum\limits\cup\{(,),|,*\}$. Some things to note about regular expressions are:
- The empty string $\epsilon$ is a regular expression
- $x$ is a regular expression for an $x\in\sum\limits$ (literals)
- If $x$ is a regular expression then $(x)$ is a regular expression
- If $x$ and $y$ are regular expression then $xy$,$x|y$ and $x^*$ are also regular expressions
We must also follow the order of operations when it comes to regular expressions. Listed below in order from highest priority to lowest:
1. $()$
2. Kleene Star
3. Concatenation
4. |

# Matching
Regular expressions are specifications for strings following a certain pattern. If the string in question follows the pattern specified by the regular expression then we can say that the regular expression matches the string. The rules for matching are:
- $\epsilon$ matches the string $\epsilon$ 
- For any $x\in\sum\limits$,$x$ matches the string $x$ 
- For any two regular expressions $x$ and $y$, $xy$ will match a string $z$ where if $z=uv$, $x$ matches $u$ and $v$ matches $y$.