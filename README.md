# SE350 Question Writer

This is a script that produces properly formatted questions for submission in SE350 from JSON. It turns this
```
{
  "title": "Basic Arithmetic",
  "question": "What is the result of this mathematical operation\n1 + 1 = ?\nUse a decimal base.",
  "feedback": "Adding numbers is an essential skill. MATH 115 and MATH 117",
  "options": [
    {"answer": 5, "points": 0, "feedback": "Incorrect answer. Revisit your basic math skills."},
    {"answer": 11, "points": 0, "feedback": "Incorrect answer. Revisit your basic math skills."},
    {"answer": 3, "points": 50, "feedback": "The question was phrased in the decimal system."},
    {"answer": 2, "points": 100, "feedback": "Correct."}
  ]
}
```
into this
```
NewQuestion,MC,
Title,"Basic Arithmetic",
QuestionText,"
What is the result of this mathematical operation
1 + 1 = ?
Use a decimal base.
",
Option,0,"5",,"Incorrect answer. Revisit your basic math skills."
Option,0,"11",,"Incorrect answer. Revisit your basic math skills."
Option,50,"3",,"The question was phrased in the decimal system."
Option,100,"2",,"Correct."
Feedback,"Adding numbers is an essential skill. MATH 115 and MATH 117",,,,
```

## Installation

You must have Ruby installed to run this script. I haven't tested many versions but I suspect it will work on Ruby 1.8.7+, which is installed on OSX and most Linux systems out of the box.

Install the `bundler` gem, which handles this project's dependencies, by running `gem install bundler`. Then use `bundler` to install this app's dependencies by running `bundle install`.

Mark the validator script as executable `chmod +x ./se350-question-writer`

## Usage

This script takes a JSON string from `stdin` and prints a validated d2l-formatted question file on `stdout`.

It can be run as `./se350-question-writer < examples/example.json > examples/example.d2l`.