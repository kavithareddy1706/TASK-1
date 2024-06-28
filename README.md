TASK-1 
To write a C Program to count the sum of numbers from 1 to n
Here is the program for counting the sum of numbers
![C PROGRAM](https://github.com/kavithareddy1706/TASK-1/assets/173707290/0a146378-fa6a-4fd3-a664-de07930febaa)
Output of the program is given below
![RESULT OF C PROGRAM](https://github.com/kavithareddy1706/TASK-1/assets/173707290/6d02b966-a7ba-4778-86d4-95e8acbf2df7)
Running the program using RISC-V
![CALCULATION OF RISC V PROCESSOR](https://github.com/kavithareddy1706/TASK-1/assets/173707290/6851096b-57e3-4e27-ac75-b97c0bdc0b18)
![USING FAST INSTURCTIONS](https://github.com/kavithareddy1706/TASK-1/assets/173707290/d26e3533-153d-42f9-af78-c9f335e7e702)

TASK-2
Write a C program for a 7 segment display driver

int segment_Pins[] = {2,3,4,5,6,7,8,9}; 
// Truth table which we saw earlier
byte segmentCode[10][8] = {
    //  a  b  c  d  e  f  g  .
    {1, 1, 1, 1, 1, 1, 0, 0},  // 0
    {0, 1, 1, 0, 0, 0, 0, 0},  // 1
    {1, 1, 0, 1, 1, 0, 1, 0},  // 2
    {1, 1, 1, 1, 0, 0, 1, 0},  // 3
    {0, 1, 1, 0, 0, 1, 1, 0},  // 4
    {1, 0, 1, 1, 0, 1, 1, 0},  // 5
    {1, 0, 1, 1, 1, 1, 1, 0},  // 6
    {1, 1, 1, 0, 0, 0, 0, 0},  // 7
    {1, 1, 1, 1, 1, 1, 1, 0},  // 8
    {1, 1, 1, 1, 0, 1, 1, 0},  // 9
};
void Display(int number) {
    for (int i = 0; i < 8; i++) {
        digitalWrite(segment_Pins[i], segmentCode[number][i]);
    }
}
void setup() {
    for (int i = 0; i < 8; i++) {
        pinMode(segment_Pins[i], OUTPUT);
    }
}
void loop() {
    for (int n = 0; n < 10; n++) {
        Display(n);
        delay(1000);
    }
}
