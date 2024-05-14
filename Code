#!/bin/bash

# Colors
RED='\033[0;31m'
GREEN='\033[0;32m'
YELLOW='\033[0;33m'
BLUE='\033[0;34m'
CYAN='\033[0;36m'
NC='\033[0m' # No Color

# Check if database file exists, if not create it
if [ ! -f mydb ]; then
    touch mydb
fi

# Function for user login
Login() {
echo -e "\n\n\n\t *************Employee************************"
echo -e "\n\n\n\t **************Management*********************"
echo -e "\n\n\n\t ***************System************************"
    echo -e "\n\n${CYAN}\t1. Login"
    echo -e "\t2. Exit${NC}"
    echo -e "${YELLOW}\tEnter choice: \c${NC}"
    read choice
    case $choice in
    1)
        clear
        echo -e "${GREEN}EMPLOYEE MANAGEMENT${NC}"
        echo -e "\t${YELLOW}Username: \c${NC}"
        read username
        echo -e "\t${YELLOW}Password: \c${NC}"
        read -s password
        if [[ "$username" == "project" && "$password" == "1234" ]]; then
            clear
            echo -e "${GREEN}EMPLOYEE MANAGEMENT${NC}"
            Introduction
        else
            clear
            echo -e "${GREEN}EMPLOYEE MANAGEMENT${NC}"
            echo -e "${RED}Username or Password is not correct, please try again...${NC}"
            Login
        fi
        ;;
    2)
        clear
        exit
        ;;
    *)
        clear
        echo -e "${GREEN}EMPLOYEE MANAGEMENT${NC}"
        Login
        ;;
    esac
}

# Function to display introduction menu
Introduction() {
    echo -e "\n\n${CYAN}\t1. Display Employee Information"
    echo -e "\t2. Add New Employee"
    echo -e "\t3. Modify Employee Information"
    echo -e "\t4. Delete Employee Information"
    echo -e "\t5. Exit${NC}"
    echo -e "${YELLOW}\tChoice: \c${NC}"
    read choice
    case $choice in
    1)
        clear
        echo -e "${GREEN}EMPLOYEE MANAGEMENT${NC}"
        Show
        ;;
    2)
        clear
        echo -e "${GREEN}EMPLOYEE MANAGEMENT${NC}"
        Insertion
        ;;
    3)
        clear
        echo -e "${GREEN}EMPLOYEE MANAGEMENT${NC}"
        Modification
        ;;
    4)
        clear
        echo -e "${GREEN}EMPLOYEE MANAGEMENT${NC}"
        Deletion
        ;;
    5)
        clear
        exit
        ;;
    *)
        clear
        echo -e "${GREEN}EMPLOYEE MANAGEMENT${NC}"
        Introduction
        ;;
    esac
}

# Function to display details of all employees
Show() {
    acheki=$(wc -l mydb | awk '{print $1}')
    if ((acheki != 0)); then
        header
        cat mydb
    else
        printf "\n\n\n\t\t\t\t${RED}NO RECORDS FOUND!${NC}\n\n\n"
    fi
    echo -e "${YELLOW}Enter any key to go back...${NC}"
    read -n 1
    clear
    echo -e "${GREEN}EMPLOYEE MANAGEMENT${NC}"
    Introduction
}

# Function to display header for employee details
header() {
    printf "\n${BLUE}Emp_ID\tFirst_Name\tLast_Name\tAddress\tDate_Of_Birth\tSex\tDepartment\tSalary\tDesignation\tJoining_Date${NC}\n"
    printf "${BLUE}-------------\t----------\t---------\t-------\t-------------\t---\t----------\t------\t-----------\t------------${NC}\n"
}

# Function to add new employee
Insertion() {
    echo "Please fill the following form: "
    printf "Employee ID : "
    read eid
    printf "First Name : "
    read fname
    printf "Last Name : "
    read lname
    printf "Address : "
    read addr
    printf "Date Of Birth : "
    read dob
    printf "Sex : "
    read sex
    printf "Department : "
    read dept
    printf "Salary : "
    read sal
    printf "Designation : "
    read des
    printf "Joining Date : "
    read jdate
    data=$(echo -e "$eid\t$fname\t$lname\t$addr\t$dob\t$sex\t$dept\t$sal\t$des\t$jdate")
    echo $data >> mydb
    printf "\nRecord successfully added."
    printf "\nEnter any key to go back..."
    read a
    clear
    echo -e "${GREEN}EMPLOYEE MANAGEMENT${NC}"
    Introduction
}

# Function to modify employee information
Modification() {
    clear
    printf "Enter Emp_ID of the employee whose record has to be modified : "
    read mod
    khojo=$(awk -v md=$mod '{if($1==md)print;}' mydb | wc -l)
    if (($khojo == 0)); then
        printf "\n\n\n\t\t\t\tNO RECORDS FOUND TO MODIFY!\n\n\n"
    else
        printf "\nOld details : \n"
        header
        awk -v md=$mod '{if($1==md)print;}' mydb
        printf "\nWhich field do you want to modify? Enter the field number: "
        read field
        printf "\nEnter new detail : "
        read nw
        awk -v f=$field -v m=$mod -v dibo=$nw '{if($1==m) $f=dibo;print;}' mydb >tmp && mv tmp mydb
        printf "\nRecord successfully modified."
        printf "\nUpdated details : \n"
        header
        awk -v md=$mod '{if($1==md)print;}' mydb
    fi
    printf "\nEnter any key to go back..."
    read a
    clear
    echo -e "${GREEN}EMPLOYEE MANAGEMENT${NC}"
    Introduction
}

# Function to delete employee information
Deletion() {
    printf "\nEnter Emp_ID which you want to delete: "
    read emp
    sed -i "/^$emp/d" mydb
    printf "\nRecord deleted successfully."
    printf "\nEnter any key to go back..."
    read a
    clear
    echo -e "${GREEN}EMPLOYEE MANAGEMENT${NC}"
    Introduction
}

# Start the script by calling the Login function
Login
