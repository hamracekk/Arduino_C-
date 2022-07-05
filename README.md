# Arduino_C-

Tasks:

02 - Arduino LEDs
03 - Arduino Buttons
04 - Arduino 7seg Display
05 - Arduino Stopwatch
06 - Arduino Running Message
Dungeon and Dragons dice


WARNING!! : It is necessary to download funshield file and import it to all arduino solutions.


02 - Arduino LEDs:

    Write a program for Arduino UNO with attached Funshield, which will animate the following pattern on the four vertical LEDs. 
    At any given moment, exactly one LED (of four) is turned on (we are starting with the topmost one). In each step of the animation, 
    the active LED moves one slot down. When it hits the bottom, it bounces and moves upwards again, until it reaches top. 
    The animation repeats itself forever.

    One step of the animation takes exactly 300ms. Do not use delay() nor delayMicroseconds() function and do not block the main loop by other means. Use millis()          function to measure, how much time actually passed.
    
03 - Arduino Buttons:

    Write a simple counter application for Arduino UNO with attached Funshield. The counter is an integer in 0-15 range, 
    which is being displayed continuously on the four-LEDs stipe on the shield. Lowest bit is displayed at bottom 
    LED (note that is led4_pin, whilst led1_pin is topmost). The first two buttons act as increment and decrement for the 
    counter in modular arithmetic (mod 16). The counter is set to 0 at the beginning (when the device boots).

    The main objective is to implement a smart behavior of the buttons as follows:

    When the first button is pressed (changes state from being up to being down), it increments the counter.
    If the button is being held down, the application waits for 1000ms and then perform another increment. 
    After that the increments will repeat periodically every 300ms until the button is released. 
    The second button works analogically, but it decrements the counter instead. The buttons work independently. 
    If they are both held, the counter is being both incremented and decremented (in due intervals).
    Example: The first button is pressed at time T and at T+2000 (ms) it is released again. 
    In this situation, the counter will be incremented at times T, T+1000, T+1300, T+1600, and T+1900.
    
04 - Arduino 7seg Display:

    Write a counter application for Arduino UNO with attached Funshield. The value of the counter will be projected 
    on 7-segment LED display so that exactly one digit is visible at any given time (i.e., we are not going to use multiplexing to show multiple digits).

    The counter holds value in 0-9999 range which should be displayed on the four-digit 7-segment LED display in standard 
    decadic format (units are the rightmost digits). Exactly one digit (one order) is lit at any given time, the order of units 
    is selected at the beginning. The third button alternates, which digit is shown (i.e., which order is selected) so the user 
    can read the whole number digit per digit. Values which do not have 4 digits (lesser than 1000) are displayed with leading 
    zeroes (e.g., value 42 is displayed as 0042).

    The first two buttons work as increment and decrement respectively modifying the counter according to the selected 
    order (as explained in the following text). The counter is modified in modular arithmetic (mod 10,000). 
    When the device is started, the counter is set to 0.

    The operations of individual buttons are:

    Button #3 selects the displayed digit (order). At the beginning, the order of units is selected (the rightmost digit). 
    Clicking the button changes the the order to tens, hundreds, thousands, and then back to units.

    Button #1 increments the currently selected digit when pressed (when the button goes down). In other words, if the order 
    of units is selected, +1 is added to the counter. If order of tens is selected, +10 is added and so on.

    Button #2 works in the same way as button #1, but it decrements the value (i.e., adds -1, -10, -100, or -1000 to the counter
    depending on currently selected order).

05 - Arduino Stopwatch:

    Design and implement a Stopwatch based on Arduino UNO with attached Funshield. The stopwatch must measure the time internally in milliseconds and display the           measured values on the 7-segment LED display with 0.1s precision (including the decimal dot, rounding down). The number should be displayed in regular decadic          format used in Czech Republic (no leading zeros except one right before the decimal dot). The stopwatch is zeroed at the beginning (i.e., displaying only 0.0          aligned right).

    Stopwatch Controls
    The stopwatch is always in one of three logical states (stopped, running, or lapped). In the stopped state, internal clock are not advanced and the display is         showing the last measured value (this state is also the initial state after boot). In the running state, the internal clock is measuring passed time and the value     on the display is updated continuously. In the lapped state, the stopwatch is still running (collecting time), but the display is frozen -- showing the value which     was actual when the lapped state was initiated. The transition diagram looks as follows:

    Button 1 performs the start/stop function. It has no bearing in the lapped state.
    Button 2 freezes/unfreezes (laps/un-laps) the time. It has no bearing in the stopped state.
    Button 3 works only in the stopped state and it resets the stopwatch (sets internal time counter to 0).
    
    
    
06 - Arduino Running Message:
    
       The objective of this assignment is to turn funshield into a message notification panel. It receives messages from the computer (via USB serial link) and              displays them on the 7-seg LED display as running text (i.e., text which is scrolling from right to left).

       The starter pack can be downloaded here. The solution.ino already holds constants for individual letter glyphs (a-z) and a basic function that displays them            individually. Please note that we do not distinguish between lowercase and uppercase since we had to mix these two to get recognizable glyphs. All non-letter          characters are displayed as empty space (blank position).

       The starter pack also contains header file input.h with SerialInputHandler structure (class) that encapsulates processing of the serial input. Its initialize()        method must be invoked in setup() and updateInLoop() method in every loop(). At the beginning and at the conclusion of scrolling of every message, the                  getMessage() will provide you with the next message to be displayed. The structure keeps the last message internally and it will return it until the next              message is sent over.

       Submit only the solution.ino file (the name must match exactly) in ReCodEx. File input.h (on the other hand) must not be submitted as ReCodEx will provide              SerialInputHandler implementation of its own designed for testing. As usual, do not use delay() nor delayMicroseconds() function and do not block the main loop        by other means.

       Displaying the Message
       Each message starts its scrolling when the display is empty (showing four empty spaces). The message moves from right to left and the interval between two              shifts is exactly 300 ms. At the end, the message must entirely leave the display (i.e., as if there are 4 spaces at the end of every message). Thus, the               display is rendered empty before the next message starts to scroll.

       Please beware, the message may have less then 4 characters or it may be even empty. Nevertheless, it is still displayed using the same algorithm (i.e., empty          string will actually cause the display to stay empty for 1200 ms).

Dungeon and Dragons dice (FINAL BIG TASK):


       The objective is to create a random number generator which will simulate dice throws in Advanced Dungeons&Dragons game. The game uses various types of                  polyhedral dices with different numbers of sides (d4, d6, d8, ...). Furthermore, a generated random number represents a sum of multiple throws. E.g., 3d6 means        that player should throw 3 times using a dice with 6 sides (cube) and take the sum of these three throws (which is a number between 3 and 18).

       The dice is controlled by 3 buttons and display the results on the 4-digit LED display. It operates in two modes. In normal mode it displays last generated            number on the LED display. In configuration mode it displays the type (and repetition) of dice being simulated. First digit (1-9) displays number of throws,            second digit displays symbol 'd', and the remaining two digits display the type of dice (d4, d6, d8, d10, d12, d20, and d100 should be supported; d100 is              displayed as '00' on the LED display).

        Button 1:
        switches the dice to normal mode
        whilst pressed down, the random data are gathered (result is being generated)
        when the button is released, a new random result has to be displayed
        
        Button 2:
        switches the dice to configuration mode
        increments the number of throws (if 9 is exceeded, the number returns to 1)
        
        Button 3:
        switches the dice to configuration mode
        changes the dice type (dices d4-d100 from the list above are cycled)
        
        It might be a good idea to show some 'activity' on the display whilst the random number is being generated (whilst the button 1) is pressed. You may show               currently computed random numbers (if they change fast enough so the user cannot possibly stop at the right number), or you may create some sort of animation           on LED display or using the other onboard LEDs.

        Remember that the probability distribution is not uniform (for more than one dice). Your simulator must use counter/time measurement of how long the button 1           has been pressed to get a random number (which follows uniform distribution). You may use additional pseudo-random generators (even Arduino built-in functions)         to assist you with this task, but the initial randomness has to be tied somehow to the button event duration.
