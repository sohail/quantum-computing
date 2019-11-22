### Quantum Interference(simulator)

(Last updated:- Tuesday, 19th of November, 2019 AT 2:44 AM, while listening to "It's so Hard" by, Anouk)

A fundamental idea in quantum computing is to control the probability a system of qubits collapses into particular measurement states

```cpp

    void normalize_amplitudes(struct amplitude amplitudes[])
    {        
        std::cout<<pow((amplitudes[0].real + amplitudes[0].imaginary*amplitudes[0].imaginary*(-1)), 2) + pow((amplitudes[1].real + amplitudes[1].imaginary*amplitudes[1].imaginary*(-1)), 2)<<std::endl;
    }    

    void print_complex_number(const struct amplitude amplitudes[])    
    {
        for (int i = 0; i < MAX_NUMBER_OF_STATES(MAX_NUMBER_OF_QUBITS); i++)
        {
            if (amplitudes[i].real < 0)
            {
                std::cout<<"-("<<amplitudes[i].real*(-1);
            }
            else 
            {
                std::cout<<"("<<amplitudes[i].real;
            }

            std::cout<<" + ";

            std::cout<<"i"<<amplitudes[i].imaginary*(-1)<<") = "<<amplitudes[i].normalized<<", real = "<<amplitudes[i].real<<", imaginary =  "<<amplitudes[i].imaginary<<std::endl;            
        }
    }
    
    // This method just calculate amplitudes and call few helper functions to display them
    void Method_random(const FunctionCallbackInfo<Value>& args)
    {
        int i = 0;

        cc_tokenizer::allocator<char> alloc_obj;
        struct amplitude *amplitudes = (amplitude*)alloc_obj.allocate(sizeof(amplitude)*MAX_NUMBER_OF_STATES(MAX_NUMBER_OF_QUBITS));

        std::random_device rd; // random device
        std::mt19937 generator(rd()); 

        // dis_real, to generate the real part of complex number
        std::uniform_real_distribution<> dis_real(-1, 1); // uniform distribution between -1 and 1, for real part of the complex number
        // dis_imaginary, to generate imaginary part of complex number and that number is assumed to be square root of actual imaginary part of complex number
        std::uniform_real_distribution<> dis_imaginary(-1, 0); // Uniform distribution between -1 and 0, for imaginary part of the complex number. This part is always negative unlike part of complex number which is real. The real part can be negative as well as negative
        
        // go through all qubits one qubit at a time, each qubit has MAX_NUMBER_OF_SPINS states 
        while (i < MAX_NUMBER_OF_STATES(MAX_NUMBER_OF_QUBITS))
        {
            // Assumpltion is that "imaginary" has a square root of actual imaginary portion of complex number
            // normalized has the number which is normalized as per the "born rule" about probability wave 
            double real = dis_real(generator), imaginary = dis_imaginary(generator), normalized = ((real + imaginary*imaginary*(-1))*(real + imaginary*imaginary*(-1)));
            
            // probability is at most 1, qubit atleast has one more state which needs its amplitude to get assigned/calculated
            if (normalized >= 1)
            {
                continue;
            }

            // the array holds amplitudes/probabilities of all states of a qubit            
            amplitudes[i].real = real;
            amplitudes[i].imaginary = imaginary;            
            amplitudes[i].normalized = normalized;
                        
            dis_real.reset();
            dis_imaginary.reset();
            
            // the amplitude/probability of the other state. The sum of all amplitudes/probabilities assigned to all states one state at a time has to be 1
            normalized = 1 - amplitudes[i].normalized;

            // we only need this for the sign or our actual real value which for now is hidden in the value of "normalized"    
            real = dis_real(generator);            
            imaginary = dis_imaginary(generator);
                            
            if (real < 0)
            {
                real = (-1)*(sqrt(normalized)*(-1) + imaginary*imaginary*(-1));                 
            }
            else
            {                    
                real = (-1)*(sqrt(normalized) + imaginary*imaginary*(-1));                
            }

            // assign amplitude to the other spin or state of qubit    
            amplitudes[i + 1].real = real;
            amplitudes[i + 1].imaginary = imaginary;
            amplitudes[i + 1].normalized = normalized;
                        
            i = i + MAX_NUMBER_OF_SPINS;
        } 

        print_complex_number(amplitudes);
        normalize_amplitudes(amplitudes); 
    }    


```


```cpp

    /* This method generates interference */
    /*
        TODO. Random number should be always be complex... (a + bi)
        
        - Generate a random number n(a fraction), 
          consider this number to be an square root of number n*n 
          Further consider that number n*n is negative(-1*n*n) 
          Now take the square root of -1*n*n 
          That square root would be ni(n multiples of i) 
          This is the imaginary part of a complex number   	
    */
    void Method_random(const FunctionCallbackInfo<Value>& args)
    {        
        double coefficient, coefficients[MAX_COEFFICIENT], table[9];

        std::random_device rd; // random device
        std::mt19937 generator(rd()); 
        std::uniform_real_distribution<> dis(0, 1); //uniform distribution between 0 and 1
        
        for (int i = 0; i < 9; i++)
        {
            table[i] = dis(generator);
        }

        /*for (int i = 0; i < 9; i++)
        {
            std::cout<<table[i]<< ", ";
        }*/

        table[0] = (table[0] + table[1] + table[2]) / 3;
        table[1] = (table[3] + table[4] + table[5]) / 3;
        table[2] = (table[6] + table[7] + table[8]) / 3;

        //std::cout<<std::endl<<std::endl;

        std::cout<<table[0]<<", "<<table[1]<<", "<<table[2]<<std::endl<<std::endl;

        dis.reset();

        while (1)
        {              
            coefficient = dis(generator);

            if (coefficient*coefficient < 1)
            {
                coefficients[0] = coefficient;

                break;                
            }            
        }
        
        coefficients[1] = sqrt(1 - coefficients[0]*coefficients[0]);

        if (table[0] >= table[2])
        {
            coefficients[0] = coefficients[0] * (-1);
        }

        if (table[1] >= table[2])
        {
            coefficients[1] = coefficients[1] * (-1);
        }

        std::cout<<coefficients[0]<<" + "<<coefficients[1]<<" = "<<coefficients[0]*coefficients[0] + coefficients[1]*coefficients[1]<<std::endl;                
    }

````


    
