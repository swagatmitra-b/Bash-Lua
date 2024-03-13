# Preface

This tutorial presumes you are already familiar the terminal and basic linux commands. Every shell command is valid Bash syntax and can be executed in a Bash script in the same way as it is executed in the terminal. Bash scripting simply allows you to leverage the power of terminal commands to write programs that suit your needs.

### Comments

```bash
# this is a comment!
```

### Variables

```bash
name="Swagat"
message="loves you"
age=20
isTall=false

echo $name $age $isTall "$name $message" # this is a print statement
```

### Input

```bash
# input in a new line
echo "enter your name"
read name
echo $name

# the `r` flag treats backslashes as normal characters
echo "enter file path"
read -r path
echo $path

# input in the same line
read -p "enter your age" age
echo $age
```

#### Command Line Arguments

```bash
name=$1
age=$2
country=$1

echo "name:" $1 "age:" $2 "country:" $3
```

> ~$ ./bash.sh swagat 20 india <br>
> name: swagat age: 20 country: india

### Command Substitution

```bash
data=$(cat bash.sh) # data now stores the output of the `cat bash.sh` command

echo $data
```

### Control Flow and Logical Operators

```bash
name="Swagat"
age=20
lovesLinux=true

if [[ $age -gt 20 ]]; then
    echo "age is greater than 20"
elif [[ $age -lt 20 ]]; then
    echo "age is less than 20"
else
    echo "age is equal to 20"
fi


# compare strings
if [[ $name == "Swagat" ]]; then
    echo "Hello Swagat"
else
    echo "Hello stranger!"
fi

if [[ $age == 20 ]] && [[ $lovesLinux == true ]]; then
    echo "and operation"
elif [[ $age != 20 ]] || [[ $lovesLinux == false ]]; then
    echo "or operation"

if ! $lovesLinux ; then
    echo "unappealing"
fi
```

#### Arrays

```bash
arr=("I" "love" "you")

echo ${arr[1]} # love

arr[1]="adore" # ("I" "adore" "you")

unset arr[0] # ("adore" "you")

arr+=("the most") # ("adore" "you" "the most")

# Iterating over array
for word in ${arr[@]}; do
    echo $word
done

for ((i = 0; i<${#arr[@]}; i++)); do # ${#arr[@]} is the length of the array
    echo ${arr[i]}
done
```

#### Associative Arrays (HashMaps)

```bash
declare -A hash_map # initialize Hash Map

my_hash_map["name"]="Swagat"
my_hash_map["age"]=20

echo ${my_hash_map[name]}
echo ${my_hash_map[age]}

echo ${!my_hash_map[@]} # age name
echo ${my_hash_map[@]} # 20 Swagat

# Iterating over the Hash Map
for key in ${!my_hash_map[@]}; do
    echo "Key: $key, Value: ${my_hash_map[$key]}"
done

# To eheck if a key (age) exists in Hash Map
if [[ -v my_hash_map[age] ]]; then
    echo "exists"
fi

# To delete an entry
unset my_hash_map[age]
```

#### Loops

```bash
# prints all numbers from 1 to 10, both inclusive
for i in {1..10}; do
   echo $i
done

# prints all numbers from 0 to 9
for ((i = 0; i<10; i++)); do
    echo $i
done

# while loops
count=1
while (( $count < 10 )); do
    echo $count
    ((count++)) # incrementer
done
```

### Functions

```bash
getCompliment() {
    local position=$1 # local variable
    local compliment=$2

    echo "You placed $position!. $compliment!"
}

result=$(getCompliment "first" "You are the best") # getCompliment "first" "You are the best" -> function call

echo $result
```

### Sleep

```bash
echo "I'll wait for 2"

sleep 2

echo "seconds" # prints after 2 seconds
```

### Exit

```bash
exit 1 # exit program with error

exit 0 # exit program with success
```

### Lua
