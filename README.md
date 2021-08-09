#SOLID

-- S - single responsiablity --

Save user credit card endpoint

    ICreditCardService interface {
        void saveCreditCard()
        //don't include validUserInput() here 
    } 



-- O - Open and closed --

    public class creditCardService: ICreditCardService

        public creditCardService(Validators[] validators){

            public saveCreditCard(){

                //validate all validators
                foreach(validator in validators){
                    validator.validate();
                }
            }
        }
    }



-- L - Liskov substitution --

Inheritance and overwirting doesn't break the API

    public class Animal {
        virtual void makeNoise();
    }

    public class RubberDuck: Animal {
        public override void makeNoise(){
            //I can't make noise
            throw NoImplementationException();
        }
    }



-- I - Interface Segragation --

Similar to SRP - 

    ICreditCardService interface {
        void saveCreditCard()
        
        I - Interface Segragation - (//don't include validUserInput() here )
    } 


-- D - dependency injection --

Use contract instead of class instance for parameters
So you can decide what implementation to pass, enable unit testing with mock data

    public class creditCardService: ICreditCardService

        public creditCardService(IValidators[] validators, ICreditCardRepo creditCardRepo){

            public saveCreditCard(){

                //validate all validators
                foreach(validator in validators){
                    validator.validate();
                }

                //save to repo
                creditCardRepo.save();
            }
        }
    }
