### Quantum Interference(simulator)

(Last updated:- Tuesday, 19th of November, 2019 AT 2:44 AM, while listening to "It's so Hard" by, Anouk)

A fundamental idea in quantum computing is to control the probability a system of qubits collapses into particular measurement states


```

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


    
