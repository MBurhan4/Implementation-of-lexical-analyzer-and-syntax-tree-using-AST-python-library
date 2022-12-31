# Implementation-of-lexical-analyzer-and-syntax-tree-using-AST-python-library
# MODULE 1; 

Implementation of lexical analyzer
Tokenization of expression (expression can be i.e a + (b*c) or 3+ (5*2) digits, alphabets, characters ) 
Building regex for the expression 
 Output tags/ tokens of the expression (i.e. ['a', '+', '(', 'b', '*', 'c', ')'] ). 

# Solution and implementation; 

The lexical analyzer can be implemented using the series of the following steps; 

1. Variable declarations and initialization 

2 Function usage 

3  Tokenization of the expression 

4. Building regex for the expression 

5- Output tags/tokens of the expression 

 

# Python code;; 

 

import re 

 
 

def lex(input_string): 

  tokens = [] 

  # Define regular expressions for each token 

  digit_pattern = r'\d+' 

  alphabet_pattern = r'[a-zA-Z]+' 

  character_pattern = r'\W+' 

 
 

  # Find all the tokens in the input string 

  for token in re.findall(digit_pattern + '|' + alphabet_pattern + '|' + character_pattern, input_string): 

    tokens.append(token) 

  return tokens 

 
 

print(lex("a + (b*c)")) 

# Output;

 ![module 1 output](https://user-images.githubusercontent.com/92621862/210150139-47f14771-d639-47ba-a35a-cb455abef9e3.PNG)
 
# Module 2; 

Implementation of syntax tree using AST library of python Note: For this task you are required to explore python AST library: 1. https://docs.python.org/3/library/ast.html 2. https://www.pythonpool.com/python-ast/ 

 

# Solution and implementation; 

In Python, it is for the most part prescribed to utilize snake_case for variable names, and that implies 

utilizing every lowercase letter and isolating words with highlights. For instance, "syntax_tree" 

or on the other hand "node_value". 

It is likewise a decent practice to introduce factors at the hour of statement, particularly when they 

are being pronounced in a capability or technique. This assists with guaranteeing that the factors are consistently 

introduced and have a known worth when they are utilized in the code.  To implement a syntax tree, you will need to define a class or structure to represent the nodes of the tree. Each node should have at least a "value" attribute to store the value of the node, and possibly additional attributes to store the children of the node or other relevant information. 

# Python code; 

#Import name is a class defined in the ast module that is used to express the import statement in python in the form of an Abstract Syntax Tree. When the parse() method of ast is called on a Python source code that contains the import keyword, the ast. 

import ast 

 
 

def create_ast(source_code): 

  # Parse the source code and create an AST 

   

  tree = ast.parse(source_code) 

 
 

  # Print the AST 

  #This is a tool and a library to work with Abstract Syntax Tree (AST) of source code in Python. It can be used to explore AST, inspect nodes and process them. 

  print(ast.dump(tree)) 

 
 

source_code = """ 

def add(x, y): 

  return x + y 

""" 

 
 

create_ast(source_code) 

# Output;

![module 2 output](https://user-images.githubusercontent.com/92621862/210150166-075bd580-8f39-4cf1-97d5-14791140acc1.PNG)

# Another code; 

class SyntaxTreeNode: 

def init(self, value, right=None, left=None): 

self.value = value 

self.left = left 

self.right = right 

def create_syntax_tree(code): 

tree = ast.parse(code) 

root = None 

for node in ast.walk(tree): 

if isinstance(node, ast.Assign): 

root = SyntaxTreeNode(node.targets[0].id) 

left = create_syntax_tree_node(node.value) 

root.left = left 

return root 

def create_syntax_tree_node(node): 

if isinstance(node, ast.Num): 

return SyntaxTreeNode(node.n) 

elif isinstance(node, ast.BinOp): 

left = create_syntax_tree_node(node.left) 

right = create_syntax_tree_node(node.right) 

return SyntaxTreeNode(node.op.class.name, left, right) 


 
