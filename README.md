Download Link : https://programming.engineering/product/timed-lab-1-arithmetic-logic-units/

# Timed-Lab-1-Arithmetic-Logic-Units
Timed Lab 1: Arithmetic Logic Units
1.1 General Rules

    You are allowed to submit this timed lab starting from the moment the assignment is released, until 75 minutes after your lab period—no more and no less (unless you have accommodations or special circumstances that have already been discussed with your professor). Gradescope submissions will remain open but you are not allowed to submit after the 75 minute period is over.

        You may submit to Gradescope as many times as you wish within your allotted test time period. We will grade your last submission.

        Submitting or resubmitting the assignment after this is a violation of the honor code—doing so will automatically incur a zero on the assignment and might be re-ferred to the Office of Student Integrity.

    Although you may ask TAs for clarification, you are ultimately responsible for what you submit. The information provided in this Timed Lab pdf takes precedence. If in doubt, please make sure to indicate any conflicting information to your TAs.

    Resources you are allowed to use during the timed lab:

        Assignment files

        Previous homework and lab submissions (this includes homework PDFs)

        Class Notes (Open Net, Open Book)

        Your mind!

    Resources you are NOT allowed to use:

        Email/messaging

        Contact in any form with any other person besides TAs

        Anything written with the use of AI-based code completion software such as GitHub Copilot or ChatGPT.

1.2 Submission Rules

    Follow the guidelines under the Deliverables section.

    You are also responsible for ensuring that what you turned in is what you meant to turn in. After submitting you should be sure to download your submission into a brand new folder and test if it works. No excuses if you submit the wrong files, what you turn in is what we grade. In addition, your assignment must be turned in via Gradescope. Under no circumstances whatsoever will we accept any email submission of an assignment. Note: if you were granted an extension you will still turn in the assignment over Gradescope.

    Do not submit links to files. We will not grade assignments submitted this way as it is easy to change the files after the submission period ends.

1.3 Is collaboration allowed?

Absolutely NOT. No collaboration is allowed for timed labs.

    Overview

In this timed lab, you will be creating an ALU with four operations. This ALU will take in two 8-bit inputs and one 2-bit op code. It will output one 8-bit output. Additionally, you will be given a circuit that you will be tasked to simplify to use the least amount of transistors possible.

2.1 Tasks and Strategy

    Set up your MUX for the ALU output.

    Build your first operation as a subcircuit, and connect it to the MUX.

    Save your work and submit it to Gradescope. This will ensure you get credit for your work even if you do not finish on time.

    Repeat steps 2 and 3 for the other three operations.

    Build your logically equivalent circuit in part B

2.2 Allowed Components

When completing this assignment, you may only use:

    basic logic gates (AND, OR, NOT, NAND, NOR),

    decoders,

    multiplexers,

    the built-in Circuitsim adders (NOT the built-in subtractors),

    splitters,

    wires,

    tunnels,

    constants,

    provided input and output pins (do NOT add any additional input or output pins)

IMPORTANT NOTE 1: After you complete each operation, you may want to save a local copy of your file as a backup. That way, if you have a problem later on, you can revert to the prior working version quickly.

IMPORTANT NOTE 2: You are allowed to and should make use of subcircuits. These subcircuits contain the circuits that you have built in other tabs of your open file. This is extremely useful to keep your ALU circuit clean and will reduce the amount of errors resulting from overlapping wires.

IMPORTANT NOTE 3: You’re allowed to use CircuitSim’s default, built-in adders (in the Arithmetic tab). So please don’t try to make your own adders, just use that one. You’re not allowed to use anything else from the Arithmetic tab (don’t try to use a subtractor; if you need a subtractor, you will need to create your own using the above-mentioned components).

IMPORTANT NOTE 4: YOU DO NOT NEED TO BUILD THE GATES OUT OF TRANSISTORS.

PLEASE, FOR YOUR OWN SAKE, DON’T DO IT. USE THE BUILT IN GATES.

    Instructions

3.1 CircuitSim Information

For this assignment, you must use the version of CircuitSim provided to you via the CS 2110 docker image. A TA should already have checked off that you can access this container. If you cannot access the container, let a TA know as soon as possible. If your file does not open in this version of CircuitSim you will receive a 0.

All changes should be made in the tl1.sim file. Do not move or rename any of the input or output pins, and do not add any additional input or output pins.

3.2 Part A: ALU Components

You will create an 8-bit ALU with the following operations, using any of the gates listed above. All numbers should be interpreted as 2’s complement. Remember: This ALU has two 8-bit inputs for A and B and one 2-bit input for OP, the op-code for the operation in the list above. It has one 8-bit output named out. These are all provided and labeled correctly, so no need to modify them. If you do modify what is provided, you risk losing compatibility with the autograder!

00.
	

B / 8
	

[Ex. B = 00011000 returns 00000011]

01.
	

(-A + 5B)
	

[Ex. A = 00000010, B =
	

00001000
	

returns 00100110]

10.
	

A % 8
	

[Ex. A =
	

00011001]
	

returns 00000001]

11.
	

(A>0)?A:B
	

[Ex. A =
	

11001010,
	

B =
	

00110001
	

returns 00110001]

Below are descriptions to elaborate more on the problems above. If you’re still having trouble comprehending exactly what the question is asking after reading below, please ask one of your TAs for clarification.

    In the B / 8 operation, note that if B is not divisible by 8, round down to the next lowest integer. For example, -1/8 and -7/8 should both result in -1 while 9/8 and 15/8 should result in 1. This operation also depends solely on the B input. It should NOT rely on A being a particular value.

    For the A % 8 operation, you need to return the result of A mod 8 (A modulo 8). If you are trying to verify your results, recall how a negative number is modded. Additionally, it is important to note that all results of modding are positive. Therefore, think about if your result will be signed or unsigned. Ex. -3 mod 8 = 5 (-3 = -1 * 8 + 5). This operation also depends solely on the A input. It should NOT rely on B being a particular value.

    For the if statement (A > 0) ? return A : return B, ensure that you are not considering 0 as a positive number when checking signs.

    The provided autograder will check the op-codes according to the order listed above:

(00)2 →− B / 8, (01)2 →− (-A + 5B), (10)2 →− A % 8, and (11)2 →− if (A > 0) ? return A : return B and thus it is important that the operations are in this exact order.

3.3 Part B: Gate Substitution

AB + A’B’ is a sum of products (SOP) expression. A circuit for this expression can be found under the simplification tab in tl1.sim. Due to current supply-chain shortages, CS 2110 students only have access to basic NAND and OR gates. These gates cannot be modified by negating their inputs with bubbles. Convert the given circuit to a logically equivalent one that contains only these gates. Use of bubbles to negate the inputs to these gates may result in a zero for this portion of the timed lab.

    Checking your work

You can run the autograder in Docker by navigating to the directory containing tl1.sim and running:

java -jar tl01-tester.jar

Note: CircuitSim autograders only show failing test cases and do not provide a results summary at the end. There are roughly 2, 048 tests per operation, so the terminal output may get flooded. The final line may state something similar to [8184 more failures omitted]. If you want a quick estimate of whether or not your operation passed, just observe how many failures are left. Upload to gradescope for a more detailed summary of test cases.

    Deliverables

Please upload the following files onto the assignment on Gradescope:

    tl1.sim
