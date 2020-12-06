# chain-ops-octave
Simple chaining of operations (a.k.a. pipe operator) in octave

There is no need for an elaborate pkg or fancy operator to do this.  
It's a very simple function and looks perfectly clean to use. Here it is:

    pkg load miscellaneous   % provides reduce function
    evalf = @(v, f) f{1}(v);
    chain = @(v, varargin) reduce( evalf, varargin, v );

That's it!

Example:

    add = @(x) @(y) x + y;

    L = [4,1,8,8,11,-68,19,11,14,8,0,-67];

    chain( L
           , add(100)
           , @char
           , @tolower
           , @strsplit   )

    # outputs:
    #   ans =
    #   {
    #     [1,1] = hello
    #     [1,2] = world!
    #   }


See also: [Simple chaining of operations (a.k.a. pipe operator) in python](https://github.com/tpapastylianou/chain-ops-python)
