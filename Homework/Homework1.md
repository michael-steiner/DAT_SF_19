


1. Using chipotle.tsv in the data subdirectory:

    i. Look at the head and the tail, and think for a minute about how the data is structured. What do you think each column means? What do you think each row means? 
    
    My Answers:
    The command **head chipotle.tsv** is used to look at the head of the file, and **tail chipotle.tsv** is used to look at the tail. The columns: 

    **order_id** is an integer that indicates a unique order. 

    **quantity** is the number of the particular item which was ordered.

    **item_name** is the generic type of item

    **choice_description** indicates the specific details regarding the ordered item

    **item_price** is the cost of the item



     The rows are item details corresponding to orders - note that mutiple rows may correspond to a single order if mutiple items were ordered. 

     ii. How Many order do there appear to be? 
     My Answer:
     Using  **tail chipotle.tsv**, we can see that the value of order_id, at the end of the file, is 1834. And it looks like the file is ordered by order_id in ascending order. 

     iii How may lines are in the file?
     My Answer:
     Using **wc -l chipotle.tsv**, we can see there are 4623 lines in the file. Note that one line is a row of headers. 

     iv. Which is more polular, steak or chicken?
     My Answer:
     Using **grep 'Chicken Burrito' chipotle.tsv | wc -l**, we can see that there are 553 chicken burritos orders. Using **grep 'Steak Burrito' chipotle.tsv | wc -l**, we can see that there are 368 steak orders, so we will conclude that chicken is more polular. 

     v. Do chicken burritos more often have black beans or pinto beans?
     My Answer:
     Using **grep 'Chicken Burrito' chipotle.tsv | grep 'Black Beans' | wc -l**, we can see  that there are 282 orders with black beans, and using **grep 'Chicken Burrito' chipotle.tsv | grep 'Pinto Beans' | wc -l**, we can see that there are 105 orders with pinto beans. We conclude that black beans are ordered more. 

2. Make a list of all of the CSV or TSV files in the DAT7 repo (using a single command). Think about how wildcard characters can help you with this task.
My Answer:
Using **find . -name \*.[ct]sv**, we get the following output.
./data/airlines.csv
./data/chipotle.tsv
./data/drinks.csv
./data/hitters.csv
./data/housing-data.csv
./data/imdb_1000.csv
./data/titanic.csv
./data/ufo.csv
./data/vehicles_test.csv
./data/vehicles_train.csv
./data/yelp.csv

3. Count the number of occurrences of the word 'dictionary' (regardless of case) across all files in the DAT7 repo.
My Answer:
Using **grep -i -r 'dictionary' \* > dictionar_word_count.txt**, followed by **tr ' ' '\n' < dictionar_word_count.txt | grep -c dictionary**. The number of occurrences of the word 'dictionary' (regardless of case) is 5.

4. Optional: Use the the command line to discover something "interesting" about the Chipotle data. The advanced commands below may be helpful to you!

My Answer:
Althoug it isn not very interestign  - it did let me work with sed and awk which I have never used. 

I wan to sum the value of cost "column".  I used the following commands:

**sed 's/\$//' cost.txt > cost1.txt**  # removes the $ character from every line
**sed '1d' cost1.txt  > cost2.txt**  # deletes the first line
**cat cost2.txt  | awk '{sum+=$1} END {print sum}’**  # sum all vales

The sum is 34500.2


 