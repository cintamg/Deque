# Deque
To create double ended queue
#include<stdio.h>
#include<stdlib.h>
#define N 5
int queue[N];
int front=-1,rear=-1;
int enqueue_front(int x);
int enqueue_rear(int x);
int dequeue_front();
int dequeue_rear();
void display();
void main()
{ printf("\nDouble Ended Queue(DEQUEUE)\n");
    printf("--------------------------------");
    int ch,ch1,ch2,ele,res;
     while(1)
    {
    printf("\n1.Input Restricted Queue\n");
    printf("2.Output Restricted Queue\n");
    printf("Enter your choice\n ");
    scanf("%d",&ch);
    switch(ch)
    {
       case 1:{
               while(1){
               printf("1.Insertion at Rear \n");
               printf("2.deletion at Front \n");
               printf("3.deletion at Rear \n");
               printf("4.display queue");
               printf("\n5.exit\n");
               printf("Enter your choice\n ");
               scanf("%d",&ch1);
               switch(ch1)
               {
                   case 1:
                       printf("Enter the element you want to insert\n");
                       scanf("%d",&ele);
                       res=enqueue_rear(ele);
                       if(res==-1)
                        printf("Overflow\n");
                       else
                        printf("%d inserted successfully\n",ele);
                       break;
                   case 2:
                       res=dequeue_front();
                       if(res==-1)
                        printf("Underflow\n");
                       else
                        printf("%d deleted successfully\n",res);
                          break;
                   case 3:
                       res=dequeue_rear();
                       if(res==-1)
                        printf("Underflow\n");
                       else
                        printf("%d deleted successfully\n",res);
                          break;
                   case 4:display();
                          break;
                   case 5:exit(0);
                   default: printf("\n..invalid input..\n");
               }
               }
              }
        case 2:{
               while(1){
                printf("\n1.Insertion at Front \n");
                printf("2.Insertion at Rear \n");
                printf("3.deletion at Front\n");
                printf("4.display queue");
                printf("\n5.exit\n");
                printf("Enter your choice\n ");
                scanf("%d",&ch2);
                switch(ch2)
                {
                   case 1:
                       printf("Enter the element you want to insert\n");
                       scanf("%d",&ele);
                       res=enqueue_front(ele);
                       if(res==-1)
                        printf("Overflow\n");
                       else
                        printf("%d inserted successfully\n",ele);
                       break;
                   case 2:
                       printf("Enter the element you want to insert\n");
                       scanf("%d",&ele);
                       res=enqueue_rear(ele);
                       if(res==-1)
                        printf("Overflow\n");
                       else
                        printf("%d inserted successfully\n",ele);
                          break;
                   case 3:
                       res=dequeue_front();
                       if(res==-1)
                        printf("Underflow\n");
                       else
                        printf("%d deleted successfully\n",res);
                       break;
                   case 4:display();
                          break;
                   case 5:exit(0);
                   default: printf("\n..invalid input..\n");
                }
               }
               }
      default: printf("\n..invalid input..\n");
    }
    }
}
int enqueue_front(int x)
{
    if(front=rear+1||(front==0&&rear==N-1))
        return -1;
    else if(front==-1)
    {
        front=rear=0;
        queue[0]=x;
    }
    else if(front==0)
    {
        front=N-1;
        queue[front]=x;
    }
    else
    {
        front--;
        queue[front]=x;
    }
}
int enqueue_rear(int x)
{
    if(front=rear+1||(front==0&&rear==N-1))
        return -1;
    else if(front==-1)
    {
        front=rear=0;
        queue[0]=x;
    }
    else if(rear==N-1)
    {
        rear=0;
        queue[rear]=x;
    }
    else
    {
        rear++;
        queue[rear]=x;
    }
}
int dequeue_front()
{
    if(front==-1)
        return -1;
    int copy=queue[front];
    if(front==rear)
        front=rear=-1;
    else
        front=(front+1)%N;
    return copy;
}
int dequeue_rear()
{
   if(front==-1)
        return -1;
    int copy=queue[rear];
    if(front==rear)
        front=rear=-1;
    else if(rear==0)
        rear=N-1;
    else
        rear--;
    return copy;
}
void display()
{
    int i=front;
    if(front==-1&& rear==-1)
        printf("\nQueue is empty \n ");
    else
    {
        while(i!=rear)
        {
            printf("%d\t ",queue[i]);
            i=(i+1)%N;
        }
        printf("%d\t ",queue[rear]);
        printf("\n Front= %d ",front);
        printf("\n Rear = %d\n",rear);
    }
}
