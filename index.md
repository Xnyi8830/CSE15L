1. sign into ssh
![plot](https://github.com/Xnyi8830/CSE15L/blob/main/login.png?raw=true)

2. git clone 

```
git clone https://github.com/ucsd-cse15l-s24/lab7
```

3. run bash test.sh

![plot](https://github.com/Xnyi8830/CSE15L/blob/main/runTest.png?raw=true)


4. edit the code using vim
```
vim ListExamples.java
```
To change the code, we have to first enter insert mode.
then, we will chnage .add(s) and the last index should that should be incrementing is index2.

![plot](https://github.com/Xnyi8830/CSE15L/blob/main/vim%20code.png?raw=true)

5. run bash test.sh and all tests should pass

![plot](https://github.com/Xnyi8830/CSE15L/blob/main/passed%20test.png?raw=true)

6. commit all chnages

```
git add ListExamples.java
git commit -m “debugging”
git push
```
