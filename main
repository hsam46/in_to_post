#include <iostream>
#include <stdio.h>
#include <stdlib.h>
#define MAX 100 //設定最大數值

using namespace std;

int priority(char x){
    switch(x){
case '*': case '/': return 2;
case '+': case '-': return 1;
default: return 0;
    }
}//回傳運算子的優先順序

double cal(char op,int a,int b){
    switch(op){
case '+':
    return a+b;
case '-':
    return a-b;
case '*':
    return a*b;
case '/':
    return a/b;
    }
}//因運算子不同，對運算元的處理

void intopost(char *infix,char *postfix){
    char stack[MAX]={'\0'};
    int i=0,b=0,top=0;//迴圈計數、後序計數、堆疊計數
    for(i=0;infix[i]!='\0';i++){
        switch(infix[i]){
        case '(':
            stack[++top]=infix[i];//存入堆疊
            break;
        case '+': case '-': case '*': case '/':
            while(priority(infix[i])<=priority(stack[top])){//判斷目前運算子是否小於堆疊中的運算子
                postfix[b++]=stack[top--];//將堆疊中的運算子提出
            }
            stack[++top]=infix[i];//存入堆疊
            break;
        case ')':
            while(stack[top]!='('){//判斷堆疊是否等於'('
                    postfix[b++]=stack[top--];//將堆疊中的運算子提出
                  }
            top--;//堆疊計數-1
            break;
        default:
            postfix[b++]=infix[i];//運算元直接堆到後序式
        }
    }
    while(top>0){
        postfix[b++]=stack[top--];
    }//將剩餘堆疊中項目堆到後序式
}//中序式轉後序式

double comp(char *infix){
    int top=0;//堆疊計數
    double stack[MAX]={0.0};//堆疊
    char postfix[MAX]={'\0'};//後序式
    char tran[2]={'\0'};//暫存空間
    intopost(infix,postfix);//將中序式轉為後序式

    for(int i=0;postfix[i]!='\0';i++){
        switch(postfix[i]){
             case '+': case '-': case '*': case '/'://遇到運算子將存於堆疊運算元進行運算
                 stack[top-1]=cal(postfix[i],stack[top-1],stack[top]);
                 top--;
                 break;
             default:
                 tran[0]=postfix[i];//字元存入暫存區
                stack[++top]=atof(tran);//將暫存轉為double型態並存入堆疊
        }
    }//讀取後序式字元
    return stack[top];
}//後序式求值

int main(void){
    char infix[MAX]={'\0'},postfix[MAX]={'\0'};//中序式、後序式
    cout<<"請輸入中序式：";
    cin>>infix;
    intopost(infix,postfix);//進行中序、後序轉換
    cout<<"後序式："<<postfix<<"\n";
    cout<<"值："<<comp(infix)<<"\n";

    system("pause");
    return 0;
}
