# Sastantua

> Allosimanius Syneca is a cold, snowy, beautiful planet. It is so beautiful that if you stood on top of the Ice Crystal Pyramids of Sastantua, it is possible that your brain will fall out due to unobserved beauty. 

### A program that builds the Ice Crystal Pyramids of Sastantua in ascii characters for it's the user. The amount of pyramids to be built, and the sizes there of can be specified when that user calls the program.

![sastantua](https://user-images.githubusercontent.com/41135333/43361212-096aed1c-927e-11e8-815e-d5d0e6777507.PNG)

### Compiling and Running the Program

#### Compilation

sastantua.c is a complete program, and can be run through any C compiler to create an executable program that can be ran in the user's terminal.
```
gcc -o sastantua sastantua.c
```

#### Running the Program

The executable can be given any number of pyramids to be built when called from the command line. Size must be greater than one, and the different sizes given must be delimited by a space.

```
./sastantua 1 3 5
```

will output
```
Size 1
|  /*\
| /***\
|/**|**\

Size 3
|               /*\
|              /***\
|             /*****\
|          /***********\
|         /*************\
|        /***************\
|       /*****************\
|    /***********************\
|   /*************************\
|  /************|||************\
| /*************|||*************\
|/**************|||**************\

Size 5
|                                  /*\
|                                 /***\
|                                /*****\
|                             /***********\
|                            /*************\
|                           /***************\
|                          /*****************\
|                       /***********************\
|                      /*************************\
|                     /***************************\
|                    /*****************************\
|                   /*******************************\
|               /***************************************\
|              /*****************************************\
|             /*******************************************\
|            /*********************************************\
|           /***********************************************\
|          /*************************************************\
|      /*********************************************************\
|     /***********************************************************\
|    /****************************|||||****************************\
|   /*****************************|||||*****************************\
|  /******************************|||$|******************************\
| /*******************************|||||*******************************\
|/********************************|||||********************************\
```

If an invalid size is given an error will be printed in place of a pyramid

```
./sastantua 1 a 2
```

will output
```
Size 1
|  /*\
| /***\
|/**|**\


***Argument "a" Invalid***


Size 2
|        /*\
|       /***\
|      /*****\
|   /***********\
|  /*************\
| /***************\
|/********|********\
```

### Size Input

Intuitivly, the larger the size we give the program, the larger the pyramid generted. Our size input directly controlls the amount of **tiers** in our pyramid, and the size of the door. As with any sturdy stucture, our tiers increase in size as they near the bottom of the pyramid, and stylisticly the size of our door increases with the size of the pyramid.

#### Tier Growth

![sastantuatiers](https://user-images.githubusercontent.com/41135333/43378842-10959190-937e-11e8-8800-701656117833.png)

As can be seen in the chart above, there's a predictable progression to the size of our pyramid's tiers.

##### Row Count Incramentation
* The top tier starts at 3 rows, and every tier after the first will always have one more row than the one above it.
    * The equation for this rule is as follows
      >Number of Rows = Tier + 2
##### Character Count Incrementation
* The top tier starts at 3 characters.
* Any row within the same tier as the row above it will always contain 2 more characters that the row above it.
* The first row of any tier below the contains (current tier number + 3) more characters than the row above it if the current tier number is odd or (current tier number + 4) more characters than the row above it if the current tier number is even.
    * The equation for this rule is as follows
      > i % 2 == 0 ? i + 4 : i + 3

#### Building the Door

The door of the pyramid is
