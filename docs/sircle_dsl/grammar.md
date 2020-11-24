# Formal Grammar of Sircle

## Value Expression

```
value_expr ::= func_app binary_op func_app | unary_op func_app
func_app = value_term func_app | value_term
value_term ::= lexeme 
             | symbol_name 
             | [ value_expr ( ',' value_expr )* ]
             | '{' ( string_lexeme '->' value_expr )+ '}'
             | '{' [ effect ( ';' effect )* ] '}'
             | '(' value_expr ( ',' value_expr )* ')'
             | '(' value_expr ')'
             | if_expr
             | for_expr
effect ::= 'def' symbol_name [ ':' type_expr ] '=' value_expr
         | symbol_name '=' value_expr
         | value_expr
if_expr ::= 'if' value_expr 'then' value_expr [ 'else' value_expr ]
for_expr ::= 'for' for_comb ( ',' for_comb )* 'do' value_expr
for_comb ::= symbol_name '<-' value_expr
           | value_expr
```

## Type Expression

```
type_expr ::= type_term ( '->' type_term )*
type_term ::= primitive_type
            | symbol_name
            | '(' type_expr ')'
            | '(' type_expr ( ',' type_expr )* ')'
            | '{' [ string_lexeme ':' type_expr ( string_lexeme ':' type_expr )* ] '}'
```

## Top-level Value Binding

```
top_value_binding ::= 'def' symbol_name [ ':' type_expr ] '=' value_expr
```

## Top-level Type Binding

```
top_type_binding ::= 'type' symbol_name '=' type_expr
```