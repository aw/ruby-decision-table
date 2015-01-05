# Decision table parser

A small snippet to parse a decision table

# What's a decision table?

> [Decision tables](https://en.wikipedia.org/wiki/Decision_table) are a precise yet compact way to model complex rule sets and their corresponding actions.

# Usage

You must supply the list of conditions and your answers. It returns the matched column number.

    EXAMPLE_DECISION_TABLE = {
      :conditions => {
        'sunny'           => [0,1,0,1,nil],
        'raining'         => [0,0,1,1,nil],
        'typhoon'         => [0,0,0,0,1]
      },
      :actions => {
        'go outside'      => [1,1,1,1,0],
        'take umbrella'   => [0,0,1,1,0],
        'wear sunglasses' => [0,1,0,1,0],
        'stay home'       => [0,0,0,0,1]
      }
    }

    EXAMPLE_ANSWERS = [1, 0, 0]

    column = DecisionTable::parse(EXAMPLE_DECISION_TABLE[:conditions], EXAMPLE_ANSWERS)
    # => 1

In this example, the column is 1, therefore: go outside and wear sunglasses ;)

    EXAMPLE_DECISION_TABLE[:actions].each {|x| puts x[0] if x[1][column] == 1 }
    # go outside
    # wear sunglasses

# License

[Public Domain (Unlicense)](UNLICENSE)
