/*
  Charlton Trezevant 
  CGS 3763 - Euripides Montagne
  Homework #1 Producer-Consumer
 */

int num_iterations = 20;
int busywait_amount = 0;

int bufsize = 5;
int buf[5];

semaphore Full, Empty, Mutex;

void busy(int x){
   for(; x > 0; x--);
}

void producer(){
    int i, prod_index = 0;
    for(i = 0; i < num_iterations; i++){
            p(Empty);
            p(Mutex);
            cout << "Item " << i << " produced.\n";
            buf[prod_index] = i;
            prod_index = ++prod_index % bufsize;
            v(Mutex);
            v(Full);

            if(busywait_amount > 0);
               busy(busywait_amount);
    }
}

void consumer(){
    int i, cons_index = 0;
    for(i = 0; i < num_iterations; i++){
            p(Full);
            p(Mutex);
            cout << "Item " << buf[cons_index] << " consumed.\n";
            buf[cons_index] = -1;
            cons_index = ++cons_index % bufsize;
            v(Mutex);
            v(Empty);

            if(busywait_amount > 0);
               busy(busywait_amount);
    }
}

main(){
    initialsem(Full, 0);
    initialsem(Empty, bufsize);
    initialsem(Mutex, 1);

    cobegin {
        producer();
        consumer();
    }
}