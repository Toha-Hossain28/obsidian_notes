```c++
void sortQ(Queue::Node* Front){
    Queue::Node *p = Front;
    Queue::Node *q = Front->next;
    while(p){
        q = p->next;
        while (q)
        {
            if(p->val>q->val){
                int temp = p->val;
                p->val = q->val;
                q->val = temp;
            }
            q = q->next;
        }
        p = p->next;
    }
}
```
