# Week-7---Control-Statements
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Java Control Statements - Interactive Test</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
            min-height: 100vh;
            padding: 20px;
        }

        .container {
            max-width: 800px;
            margin: 0 auto;
            background: white;
            border-radius: 20px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.3);
            overflow: hidden;
        }

        .header {
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
            color: white;
            padding: 30px;
            text-align: center;
        }

        .header h1 {
            font-size: 2.5em;
            margin-bottom: 10px;
        }

        .student-info {
            padding: 20px;
            background: #f8f9fa;
            border-bottom: 2px solid #e9ecef;
        }

        .info-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 15px;
        }

        .info-field {
            display: flex;
            flex-direction: column;
        }

        .info-field label {
            font-weight: bold;
            color: #495057;
            margin-bottom: 5px;
            font-size: 0.85em;
        }

        .info-field input {
            padding: 10px;
            border: 2px solid #dee2e6;
            border-radius: 8px;
            font-size: 0.95em;
            transition: border-color 0.3s;
        }

        .info-field input:focus {
            outline: none;
            border-color: #f5576c;
        }

        .test-content {
            padding: 25px;
        }

        .section-title {
            background: #f5576c;
            color: white;
            padding: 12px 20px;
            margin: 25px 0 15px 0;
            border-radius: 10px;
            font-size: 1.2em;
            font-weight: bold;
        }

        .question {
            margin-bottom: 20px;
            padding: 20px;
            background: #f8f9fa;
            border-radius: 12px;
            border-left: 4px solid #f5576c;
            transition: transform 0.2s;
        }

        .question:hover {
            transform: translateX(5px);
        }

        .question-number {
            display: inline-block;
            background: #f5576c;
            color: white;
            width: 28px;
            height: 28px;
            border-radius: 50%;
            text-align: center;
            line-height: 28px;
            font-weight: bold;
            margin-right: 10px;
        }

        .question-text {
            font-size: 1.05em;
            color: #212529;
            margin-bottom: 12px;
            font-weight: 500;
        }

        .code-block {
            background: #2d3748;
            color: #e2e8f0;
            padding: 15px;
            border-radius: 8px;
            font-family: 'Courier New', monospace;
            margin: 12px 0;
            font-size: 0.95em;
            overflow-x: auto;
            border: 1px solid #4a5568;
        }

        .options {
            display: flex;
            flex-direction: column;
            gap: 8px;
        }

        .option {
            display: flex;
            align-items: center;
            padding: 12px 15px;
            background: white;
            border: 2px solid #dee2e6;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.2s;
        }

        .option:hover {
            border-color: #f5576c;
            background: #fff5f5;
        }

        .option input[type="radio"] {
            margin-right: 12px;
            width: 16px;
            height: 16px;
            cursor: pointer;
            flex-shrink: 0;
        }

        .option.correct {
            border-color: #28a745;
            background: #d4edda;
        }

        .option.wrong {
            border-color: #dc3545;
            background: #f8d7da;
        }

        .feedback {
            margin-top: 10px;
            padding: 10px;
            border-radius: 8px;
            display: none;
            font-size: 0.95em;
            font-weight: 500;
        }

        .feedback.correct {
            display: block;
            background: #d4edda;
            color: #155724;
            border: 1px solid #c3e6cb;
        }

        .feedback.wrong {
            display: block;
            background: #f8d7da;
            color: #721c24;
            border: 1px solid #f5c6cb;
        }

        .btn {
            padding: 12px 30px;
            border: none;
            border-radius: 8px;
            font-size: 1em;
            cursor: pointer;
            font-weight: bold;
            transition: all 0.3s;
            margin-top: 10px;
        }

        .btn-check {
            background: #28a745;
            color: white;
        }

        .btn-check:hover {
            background: #218838;
            transform: translateY(-1px);
        }

        .btn-primary {
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
            color: white;
            padding: 15px 40px;
            font-size: 1.1em;
        }

        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(245, 87, 108, 0.4);
        }

        .center {
            text-align: center;
            margin-top: 30px;
            margin-bottom: 20px;
        }

        .results {
            display: none;
            padding: 40px;
            text-align: center;
        }

        .score-circle {
            width: 140px;
            height: 140px;
            border-radius: 50%;
            margin: 0 auto 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 2.2em;
            font-weight: bold;
            color: white;
        }

        .score-excellent { background: linear-gradient(135deg, #11998e, #38ef7d); }
        .score-good { background: linear-gradient(135deg, #667eea, #764ba2); }
        .score-average { background: linear-gradient(135deg, #f093fb, #f5576c); }
        .score-needs { background: linear-gradient(135deg, #4facfe, #00f2fe); }

        .results h2 {
            font-size: 1.8em;
            margin-bottom: 10px;
            color: #212529;
        }

        .results p {
            color: #6c757d;
            font-size: 1.1em;
        }

        .review-box {
            margin-top: 25px;
            text-align: left;
            max-height: 400px;
            overflow-y: auto;
            padding: 0 20px;
        }

        .review-item {
            padding: 12px;
            margin-bottom: 8px;
            border-radius: 8px;
            font-size: 0.95em;
        }

        .review-correct {
            background: #d4edda;
            border-left: 4px solid #28a745;
        }

        .review-wrong {
            background: #f8d7da;
            border-left: 4px solid #dc3545;
        }

        .disabled {
            pointer-events: none;
            opacity: 0.7;
        }

        @media (max-width: 600px) {
            .info-grid {
                grid-template-columns: 1fr 1fr;
            }
            .header h1 {
                font-size: 1.8em;
            }
            .question:hover {
                transform: none;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>🔀 Java Control Statements Test</h1>
            <p>If-Else, Nested If & Switch Case</p>
        </div>

        <div class="student-info">
            <div class="info-grid">
                <div class="info-field">
                    <label for="studentName">Name</label>
                    <input type="text" id="studentName" placeholder="Your name" autocomplete="name">
                </div>
                <div class="info-field">
                    <label for="mbti">MBTI</label>
                    <input type="text" id="mbti" placeholder="e.g., INTJ" maxlength="4">
                </div>
                <div class="info-field">
                    <label for="testDate">Date</label>
                    <input type="date" id="testDate">
                </div>
                <div class="info-field">
                    <label for="scoreDisplay">Score</label>
                    <input type="text" id="scoreDisplay" value="0/20" readonly style="background: #e9ecef; font-weight: bold; text-align: center;">
                </div>
            </div>
        </div>

        <div class="test-content" id="testContent">
            
            <!-- PART I: MULTIPLE CHOICE -->
            <div class="section-title">Part I: Multiple Choice (10 items)</div>

            <div class="question" id="q1">
                <div class="question-text"><span class="question-number">1</span>Which control statement executes code only if a condition is true?</div>
                <div class="options">
                    <label class="option" onclick="selectOption(1, 0)">
                        <input type="radio" name="q1" value="0"> a) if-then
                    </label>
                    <label class="option" onclick="selectOption(1, 1)">
                        <input type="radio" name="q1" value="1"> b) switch
                    </label>
                    <label class="option" onclick="selectOption(1, 2)">
                        <input type="radio" name="q1" value="2"> c) for
                    </label>
                    <label class="option" onclick="selectOption(1, 3)">
                        <input type="radio" name="q1" value="3"> d) break
                    </label>
                </div>
                <button type="button" class="btn btn-check" onclick="checkAnswer(1, 0, 'if-then executes code block only when condition is true.')">Check Answer</button>
                <div class="feedback" id="feedback1"></div>
            </div>

            <div class="question" id="q2">
                <div class="question-text"><span class="question-number">2</span>What is the output of this code?</div>
                <div class="code-block">int number = 12;
if (number <= 10) {
    System.out.println("Less than 10");
}</div>
                <div class="options">
                    <label class="option" onclick="selectOption(2, 0)">
                        <input type="radio" name="q2" value="0"> a) Less than 10
                    </label>
                    <label class="option" onclick="selectOption(2, 1)">
                        <input type="radio" name="q2" value="1"> b) No output
                    </label>
                    <label class="option" onclick="selectOption(2, 2)">
                        <input type="radio" name="q2" value="2"> c) Error
                    </label>
                    <label class="option" onclick="selectOption(2, 3)">
                        <input type="radio" name="q2" value="3"> d) 12
                    </label>
                </div>
                <button type="button" class="btn btn-check" onclick="checkAnswer(2, 1, '12 <= 10 is false, so the if block does not execute. No output.')">Check Answer</button>
                <div class="feedback" id="feedback2"></div>
            </div>

            <div class="question" id="q3">
                <div class="question-text"><span class="question-number">3</span>Which data type CANNOT be used in a switch statement?</div>
                <div class="options">
                    <label class="option" onclick="selectOption(3, 0)">
                        <input type="radio" name="q3" value="0"> a) int
                    </label>
                    <label class="option" onclick="selectOption(3, 1)">
                        <input type="radio" name="q3" value="1"> b) char
                    </label>
                    <label class="option" onclick="selectOption(3, 2)">
                        <input type="radio" name="q3" value="2"> c) double
                    </label>
                    <label class="option" onclick="selectOption(3, 3)">
                        <input type="radio" name="q3" value="3"> d) String
                    </label>
                </div>
                <button type="button" class="btn btn-check" onclick="checkAnswer(3, 2, 'switch works with int, char, String, byte, short. NOT double or float.')">Check Answer</button>
                <div class="feedback" id="feedback3"></div>
            </div>

            <div class="question" id="q4">
                <div class="question-text"><span class="question-number">4</span>What is the output of this code?</div>
                <div class="code-block">int number = 9;
if (number >= 10) {
    System.out.println("Greater");
} else {
    System.out.println("Less");
}</div>
                <div class="options">
                    <label class="option" onclick="selectOption(4, 0)">
                        <input type="radio" name="q4" value="0"> a) Greater
                    </label>
                    <label class="option" onclick="selectOption(4, 1)">
                        <input type="radio" name="q4" value="1"> b) Less
                    </label>
                    <label class="option" onclick="selectOption(4, 2)">
                        <input type="radio" name="q4" value="2"> c) 9
                    </label>
                    <label class="option" onclick="selectOption(4, 3)">
                        <input type="radio" name="q4" value="3"> d) No output
                    </label>
                </div>
                <button type="button" class="btn btn-check" onclick="checkAnswer(4, 1, '9 >= 10 is false, so else block executes. Output: Less')">Check Answer</button>
                <div class="feedback" id="feedback4"></div>
            </div>

            <div class="question" id="q5">
                <div class="question-text"><span class="question-number">5</span>What keyword stops execution after a case in switch?</div>
                <div class="options">
                    <label class="option" onclick="selectOption(5, 0)">
                        <input type="radio" name="q5" value="0"> a) stop
                    </label>
                    <label class="option" onclick="selectOption(5, 1)">
                        <input type="radio" name="q5" value="1"> b) exit
                    </label>
                    <label class="option" onclick="selectOption(5, 2)">
                        <input type="radio" name="q5" value="2"> c) break
                    </label>
                    <label class="option" onclick="selectOption(5, 3)">
                        <input type="radio" name="q5" value="3"> d) return
                    </label>
                </div>
                <button type="button" class="btn btn-check" onclick="checkAnswer(5, 2, 'break stops execution and exits the switch statement.')">Check Answer</button>
                <div class="feedback" id="feedback5"></div>
            </div>

            <div class="question" id="q6">
                <div class="question-text"><span class="question-number">6</span>What is the output of this code?</div>
                <div class="code-block">int number = 11;
if (number <= 3) {
    System.out.println("A");
} else if (number <= 10) {
    System.out.println("B");
} else {
    System.out.println("C");
}</div>
                <div class="options">
                    <label class="option" onclick="selectOption(6, 0)">
                        <input type="radio" name="q6" value="0"> a) A
                    </label>
                    <label class="option" onclick="selectOption(6, 1)">
                        <input type="radio" name="q6" value="1"> b) B
                    </label>
                    <label class="option" onclick="selectOption(6, 2)">
                        <input type="radio" name="q6" value="2"> c) C
                    </label>
                    <label class="option" onclick="selectOption(6, 3)">
                        <input type="radio" name="q6" value="3"> d) ABC
                    </label>
                </div>
                <button type="button" class="btn btn-check" onclick="checkAnswer(6, 2, '11 <= 3 is false, 11 <= 10 is false, so else executes. Output: C')">Check Answer</button>
                <div class="feedback" id="feedback6"></div>
            </div>

            <div class="question" id="q7">
                <div class="question-text"><span class="question-number">7</span>Which case executes if no match is found in switch?</div>
                <div class="options">
                    <label class="option" onclick="selectOption(7, 0)">
                        <input type="radio" name="q7" value="0"> a) first case
                    </label>
                    <label class="option" onclick="selectOption(7, 1)">
                        <input type="radio" name="q7" value="1"> b) last case
                    </label>
                    <label class="option" onclick="selectOption(7, 2)">
                        <input type="radio" name="q7" value="2"> c) default
                    </label>
                    <label class="option" onclick="selectOption(7, 3)">
                        <input type="radio" name="q7" value="3"> d) none
                    </label>
                </div>
                <button type="button" class="btn btn-check" onclick="checkAnswer(7, 2, 'default case executes when no other case matches.')">Check Answer</button>
                <div class="feedback" id="feedback7"></div>
            </div>

            <div class="question" id="q8">
                <div class="question-text"><span class="question-number">8</span>What is an if statement inside another if statement called?</div>
                <div class="options">
                    <label class="option" onclick="selectOption(8, 0)">
                        <input type="radio" name="q8" value="0"> a) Double if
                    </label>
                    <label class="option" onclick="selectOption(8, 1)">
                        <input type="radio" name="q8" value="1"> b) Nested if
                    </label>
                    <label class="option" onclick="selectOption(8, 2)">
                        <input type="radio" name="q8" value="2"> c) Inner if
                    </label>
                    <label class="option" onclick="selectOption(8, 3)">
                        <input type="radio" name="q8" value="3"> d) Complex if
                    </label>
                </div>
                <button type="button" class="btn btn-check" onclick="checkAnswer(8, 1, 'An if inside another if is called a nested if statement.')">Check Answer</button>
                <div class="feedback" id="feedback8"></div>
            </div>

            <div class="question" id="q9">
                <div class="question-text"><span class="question-number">9</span>What happens if you forget break in a switch case?</div>
                <div class="options">
                    <label class="option" onclick="selectOption(9, 0)">
                        <input type="radio" name="q9" value="0"> a) Error occurs
                    </label>
                    <label class="option" onclick="selectOption(9, 1)">
                        <input type="radio" name="q9" value="1"> b) Only that case executes
                    </label>
                    <label class="option" onclick="selectOption(9, 2)">
                        <input type="radio" name="q9" value="2"> c) Fall-through to next cases
                    </label>
                    <label class="option" onclick="selectOption(9, 3)">
                        <input type="radio" name="q9" value="3"> d) Program stops
                    </label>
                </div>
                <button type="button" class="btn btn-check" onclick="checkAnswer(9, 2, 'Without break, execution falls through to the next case (fall-through behavior).')">Check Answer</button>
                <div class="feedback" id="feedback9"></div>
            </div>

            <div class="question" id="q10">
                <div class="question-text"><span class="question-number">10</span>Which is the correct comparison operator for "equal to" in Java?</div>
                <div class="options">
                    <label class="option" onclick="selectOption(10, 0)">
                        <input type="radio" name="q10" value="0"> a) =
                    </label>
                    <label class="option" onclick="selectOption(10, 1)">
                        <input type="radio" name="q10" value="1"> b) ==
                    </label>
                    <label class="option" onclick="selectOption(10, 2)">
                        <input type="radio" name="q10" value="2"> c) ===
                    </label>
                    <label class="option" onclick="selectOption(10, 3)">
                        <input type="radio" name="q10" value="3"> d) equals
                    </label>
                </div>
                <button type="button" class="btn btn-check" onclick="checkAnswer(10, 1, '== is the equality operator. = is assignment, === is JavaScript, equals() is for Strings.')">Check Answer</button>
                <div class="feedback" id="feedback10"></div>
            </div>

            <!-- PART II: TRUE OR FALSE -->
            <div class="section-title">Part II: True or False (7 items)</div>

            <div class="question" id="q11">
                <div class="question-text"><span class="question-number">11</span>An if-else statement can only have one else block.</div>
                <div class="options">
                    <label class="option" onclick="selectOption(11, 'true')">
                        <input type="radio" name="q11" value="true"> True
                    </label>
                    <label class="option" onclick="selectOption(11, 'false')">
                        <input type="radio" name="q11" value="false"> False
                    </label>
                </div>
                <button type="button" class="btn btn-check" onclick="checkTF(11, true, 'True - One if can have only one else, but multiple else-if blocks.')">Check Answer</button>
                <div class="feedback" id="feedback11"></div>
            </div>

            <div class="question" id="q12">
                <div class="question-text"><span class="question-number">12</span>The switch statement works with String values in Java.</div>
                <div class="options">
                    <label class="option" onclick="selectOption(12, 'true')">
                        <input type="radio" name="q12" value="true"> True
                    </label>
                    <label class="option" onclick="selectOption(12, 'false')">
                        <input type="radio" name="q12" value="false"> False
                    </label>
                </div>
                <button type="button" class="btn btn-check" onclick="checkTF(12, true, 'True - Since Java 7, switch supports String values.')">Check Answer</button>
                <div class="feedback" id="feedback12"></div>
            </div>

            <div class="question" id="q13">
                <div class="question-text"><span class="question-number">13</span>Nested if statements can only be nested 2 levels deep.</div>
                <div class="options">
                    <label class="option" onclick="selectOption(13, 'true')">
                        <input type="radio" name="q13" value="true"> True
                    </label>
                    <label class="option" onclick="selectOption(13, 'false')">
                        <input type="radio" name="q13" value="false"> False
                    </label>
                </div>
                <button type="button" class="btn btn-check" onclick="checkTF(13, false, 'False - You can nest if statements as many levels as needed (though deep nesting is bad practice).')">Check Answer</button>
                <div class="feedback" id="feedback13"></div>
            </div>

            <div class="question" id="q14">
                <div class="question-text"><span class="question-number">14</span>The default case in switch must always be the last case.</div>
                <div class="options">
                    <label class="option" onclick="selectOption(14, 'true')">
                        <input type="radio" name="q14" value="true"> True
                    </label>
                    <label class="option" onclick="selectOption(14, 'false')">
                        <input type="radio" name="q14" value="false"> False
                    </label>
                </div>
                <button type="button" class="btn btn-check" onclick="checkTF(14, false, 'False - default can be anywhere, but it is convention to place it last.')">Check Answer</button>
                <div class="feedback" id="feedback14"></div>
            </div>

            <div class="question" id="q15">
                <div class="question-text"><span class="question-number">15</span>An if statement without braces can only execute one statement.</div>
                <div class="options">
                    <label class="option" onclick="selectOption(15, 'true')">
                        <input type="radio" name="q15" value="true"> True
                    </label>
                    <label class="option" onclick="selectOption(15, 'false')">
                        <input type="radio" name="q15" value="false"> False
                    </label>
                </div>
                <button type="button" class="btn btn-check" onclick="checkTF(15, true, 'True - Without braces {}, only the immediate next statement belongs to the if.')">Check Answer</button>
                <div class="feedback" id="feedback15"></div>
            </div>

            <div class="question" id="q16">
                <div class="question-text"><span class="question-number">16</span>The else-if statement allows checking multiple conditions in sequence.</div>
                <div class="options">
                    <label class="option" onclick="selectOption(16, 'true')">
                        <input type="radio" name="q16" value="true"> True
                    </label>
                    <label class="option" onclick="selectOption(16, 'false')">
                        <input type="radio" name="q16" value="false"> False
                    </label>
                </div>
                <button type="button" class="btn btn-check" onclick="checkTF(16, true, 'True - else-if chains allow testing multiple conditions until one is true.')">Check Answer</button>
                <div class="feedback" id="feedback16"></div>
            </div>

            <div class="question" id="q17">
                <div class="question-text"><span class="question-number">17</span>Switch case values must be constant or literal values.</div>
                <div class="options">
                    <label class="option" onclick="selectOption(17, 'true')">
                        <input type="radio" name="q17" value="true"> True
                    </label>
                    <label class="option" onclick="selectOption(17, 'false')">
                        <input type="radio" name="q17" value="false"> False
                    </label>
                </div>
                <button type="button" class="btn btn-check" onclick="checkTF(17, true, 'True - Case values must be compile-time constants, not variables.')">Check Answer</button>
                <div class="feedback" id="feedback17"></div>
            </div>

            <!-- PART III: CODE TRACING -->
            <div class="section-title">Part III: Code Tracing (3 items)</div>

            <div class="question" id="q18">
                <div class="question-text"><span class="question-number">18</span>What is the output?</div>
                <div class="code-block">int number = 50;
String size;

switch (number) {
    case 39: size = "Small"; break;
    case 42: size = "Medium"; break;
    case 44: size = "Large"; break;
    default: size = "Unknown"; break;
}
System.out.println(size);</div>
                <div class="options">
                    <label class="option" onclick="selectOption(18, 0)">
                        <input type="radio" name="q18" value="0"> a) Small
                    </label>
                    <label class="option" onclick="selectOption(18, 1)">
                        <input type="radio" name="q18" value="1"> b) Medium
                    </label>
                    <label class="option" onclick="selectOption(18, 2)">
                        <input type="radio" name="q18" value="2"> c) Large
                    </label>
                    <label class="option" onclick="selectOption(18, 3)">
                        <input type="radio" name="q18" value="3"> d) Unknown
                    </label>
                </div>
                <button type="button" class="btn btn-check" onclick="checkAnswer(18, 3, '50 does not match 39, 42, or 44, so default executes. Output: Unknown')">Check Answer</button>
                <div class="feedback" id="feedback18"></div>
            </div>

            <div class="question" id="q19">
                <div class="question-text"><span class="question-number">19</span>What is the output of this nested if?</div>
                <div class="code-block">double n1 = 5.0, n2 = 4.5, n3 = -5.3, largest;

if (n1 >= n2) {
    if (n1 >= n3) largest = n1;
    else largest = n3;
} else {
    if (n2 >= n3) largest = n2;
    else largest = n3;
}
System.out.println(largest);</div>
                <div class="options">
                    <label class="option" onclick="selectOption(19, 0)">
                        <input type="radio" name="q19" value="0"> a) 5.0
                    </label>
                    <label class="option" onclick="selectOption(19, 1)">
                        <input type="radio" name="q19" value="1"> b) 4.5
                    </label>
                    <label class="option" onclick="selectOption(19, 2)">
                        <input type="radio" name="q19" value="2"> c) -5.3
                    </label>
                    <label class="option" onclick="selectOption(19, 3)">
                        <input type="radio" name="q19" value="3"> d) 0
                    </label>
                </div>
                <button type="button" class="btn btn-check" onclick="checkAnswer(19, 0, '5.0 >= 4.5 is true, 5.0 >= -5.3 is true, so largest = 5.0')">Check Answer</button>
                <div class="feedback" id="feedback19"></div>
            </div>

            <div class="question" id="q20">
                <div class="question-text"><span class="question-number">20</span>What is the output?</div>
                <div class="code-block">int x = 15;
if (x > 20) {
    System.out.println("A");
} else if (x > 10) {
    System.out.println("B");
} else if (x > 5) {
    System.out.println("C");
} else {
    System.out.println("D");
}</div>
                <div class="options">
                    <label class="option" onclick="selectOption(20, 0)">
                        <input type="radio" name="q20" value="0"> a) A
                    </label>
                    <label class="option" onclick="selectOption(20, 1)">
                        <input type="radio" name="q20" value="1"> b) B
                    </label>
                    <label class="option" onclick="selectOption(20, 2)">
                        <input type="radio" name="q20" value="2"> c) C
                    </label>
                    <label class="option" onclick="selectOption(20, 3)">
                        <input type="radio" name="q20" value="3"> d) D
                    </label>
                </div>
                <button type="button" class="btn btn-check" onclick="checkAnswer(20, 1, '15 > 20 is false, 15 > 10 is true, so "B" prints. Rest is skipped.')">Check Answer</button>
                <div class="feedback" id="feedback20"></div>
            </div>

            <div class="center">
                <button type="button" class="btn btn-primary" onclick="submitTest()">Submit Test</button>
            </div>
        </div>

        <div class="results" id="results">
            <div class="score-circle" id="scoreCircle">0</div>
            <h2 id="resultTitle">Test Completed!</h2>
            <p id="resultMessage">Check your results below</p>
            <button type="button" class="btn btn-primary" onclick="retakeTest()">Retake Test</button>
            <div class="review-box" id="reviewBox"></div>
        </div>
    </div>

    <script>
        // Initialize
        let score = 0;
        let answered = new Set();
        let checkedQuestions = new Set();

        // Set today's date on load
        document.addEventListener('DOMContentLoaded', function() {
            document.getElementById('testDate').valueAsDate = new Date();
        });

        function selectOption(qNum, value) {
            // Visual feedback for selection
            const question = document.getElementById('q' + qNum);
            const options = question.querySelectorAll('.option');
            
            options.forEach(opt => {
                opt.style.background = '';
                opt.style.borderColor = '';
            });
            
            event.currentTarget.style.background = '#fff5f5';
            event.currentTarget.style.borderColor = '#f5576c';
        }

        function checkAnswer(qNum, correctIndex, explanation) {
            const options = document.getElementsByName('q' + qNum);
            const feedback = document.getElementById('feedback' + qNum);
            let selected = -1;
            
            // Find selected answer
            for (let i = 0; i < options.length; i++) {
                if (options[i].checked) {
                    selected = parseInt(options[i].value);
                    break;
                }
            }

            // Validation
            if (selected === -1) {
                alert('Please select an answer first!');
                return;
            }

            // Prevent rechecking
            if (checkedQuestions.has(qNum)) {
                alert('You already checked this question!');
                return;
            }

            const optionLabels = document.querySelectorAll(`#q${qNum} .option`);
            
            // Clear previous styles
            optionLabels.forEach(opt => {
                opt.classList.remove('correct', 'wrong');
                opt.style.pointerEvents = 'none';
            });

            const isCorrect = selected === correctIndex;
            
            // Apply styles
            optionLabels[correctIndex].classList.add('correct');
            if (!isCorrect) {
                optionLabels[selected].classList.add('wrong');
            }

            // Show feedback
            feedback.className = isCorrect ? 'feedback correct' : 'feedback wrong';
            feedback.innerHTML = isCorrect ? 
                '✓ Correct! ' + explanation : 
                '✗ Wrong. ' + explanation;
            feedback.style.display = 'block';

            // Update score
            if (isCorrect) {
                score++;
            }
            answered.add(qNum);
            checkedQuestions.add(qNum);
            updateScore();
        }

        function checkTF(qNum, correctValue, explanation) {
            const options = document.getElementsByName('q' + qNum);
            const feedback = document.getElementById('feedback' + qNum);
            let selected = null;

            // Find selected
            for (let i = 0; i < options.length; i++) {
                if (options[i].checked) {
                    selected = options[i].value === 'true';
                    break;
                }
            }

            if (selected === null) {
                alert('Please select True or False!');
                return;
            }

            if (checkedQuestions.has(qNum)) {
                alert('You already checked this question!');
                return;
            }

            const optionLabels = document.querySelectorAll(`#q${qNum} .option`);
            optionLabels.forEach(opt => {
                opt.classList.remove('correct', 'wrong');
                opt.style.pointerEvents = 'none';
            });

            const isCorrect = selected === correctValue;
            
            // True is index 0, False is index 1
            const correctIndex = correctValue ? 0 : 1;
            optionLabels[correctIndex].classList.add('correct');
            
            const selectedIndex = selected ? 0 : 1;
            if (!isCorrect) {
                optionLabels[selectedIndex].classList.add('wrong');
            }

            feedback.className = isCorrect ? 'feedback correct' : 'feedback wrong';
            feedback.innerHTML = isCorrect ? 
                '✓ Correct! ' + explanation : 
                '✗ Wrong. ' + explanation;
            feedback.style.display = 'block';

            if (isCorrect) {
                score++;
            }
            answered.add(qNum);
            checkedQuestions.add(qNum);
            updateScore();
        }

        function updateScore() {
            const scoreDisplay = document.getElementById('scoreDisplay');
            if (scoreDisplay) {
                scoreDisplay.value = score + '/20';
            }
        }

        function submitTest() {
            const name = document.getElementById('studentName').value.trim();
            
            if (!name) {
                alert('Please enter your name before submitting!');
                document.getElementById('studentName').focus();
                return;
            }

            const percentage = Math.round((score / 20) * 100);
            const circle = document.getElementById('scoreCircle');
            const title = document.getElementById('resultTitle');
            const message = document.getElementById('resultMessage');

            // Update score circle
            circle.textContent = score + '/20';
            circle.className = 'score-circle';

            // Determine rating
            if (percentage >= 90) {
                circle.classList.add('score-excellent');
                title.textContent = '🎉 Excellent!';
                message.textContent = percentage + '% - Master of Control Statements!';
            } else if (percentage >= 75) {
                circle.classList.add('score-good');
                title.textContent = '👍 Very Good!';
                message.textContent = percentage + '% - Great understanding!';
            } else if (percentage >= 60) {
                circle.classList.add('score-average');
                title.textContent = '👌 Good!';
                message.textContent = percentage + '% - Keep practicing if-else and switch!';
            } else {
                circle.classList.add('score-needs');
                title.textContent = '📚 Study More!';
                message.textContent = percentage + '% - Review control statements!';
            }

            // Generate review
            const reviewBox = document.getElementById('reviewBox');
            let reviewHTML = '<h3>Question Review:</h3>';
            
            const wrongAnswers = [];
            for (let i = 1; i <= 20; i++) {
                const feedback = document.getElementById('feedback' + i);
                if (!checkedQuestions.has(i)) {
                    wrongAnswers.push(i);
                } else if (feedback && feedback.classList.contains('wrong')) {
                    wrongAnswers.push(i);
                }
            }

            if (wrongAnswers.length === 0) {
                reviewHTML += '<div class="review-item review-correct">🌟 Perfect! All answers correct!</div>';
            } else {
                reviewHTML += '<div class="review-item review-wrong">Questions to review: ' + wrongAnswers.join(', ') + '</div>';
                reviewHTML += '<p style="margin-top: 10px; color: #666;">Scroll up to see detailed explanations for each question.</p>';
            }

            reviewBox.innerHTML = reviewHTML;

            // Show results
            document.getElementById('testContent').style.display = 'none';
            document.getElementById('results').style.display = 'block';
            
            // Scroll to top
            window.scrollTo(0, 0);
        }

        function retakeTest() {
            // Reset all variables
            score = 0;
            answered.clear();
            checkedQuestions.clear();
            
            // Reset UI
            updateScore();
            document.getElementById('testContent').style.display = 'block';
            document.getElementById('results').style.display = 'none';
            
            // Clear all selections and feedback
            for (let i = 1; i <= 20; i++) {
                // Clear radio buttons
                const options = document.getElementsByName('q' + i);
                for (let j = 0; j < options.length; j++) {
                    options[j].checked = false;
                }
                
                // Clear feedback
                const feedback = document.getElementById('feedback' + i);
                if (feedback) {
                    feedback.style.display = 'none';
                    feedback.className = 'feedback';
                    feedback.innerHTML = '';
                }
                
                // Reset option styles
                const optionLabels = document.querySelectorAll('#q' + i + ' .option');
                optionLabels.forEach(opt => {
                    opt.classList.remove('correct', 'wrong');
                    opt.style.pointerEvents = 'auto';
                    opt.style.background = '';
                    opt.style.borderColor = '';
                });
            }
            
            // Scroll to top
            window.scrollTo(0, 0);
        }
    </script>
</body>
</html>
