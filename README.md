# library-Management-System-using-Bash-Script-language-
#!/bin/bash
echo -e " ****************************************"
echo -e " ****************************************"
echo -e "                   *"
echo -e "   *    Library Management System    *"
echo -e "                   *"
echo -e " ****************************************"
echo -e " ****************************************"
t=100
while [ $t -ne 0 ] 
do 

echo "1. View The List of All Books and Authors Details "
echo "2. Insert Books and Author Records "
echo "3. Delete Books Records "
echo "4. Modify a Book Records "
echo "5. Searching of Particular Book"
echo "6. Exit"
echo " Please Enter The Choice: "
read d 
case $d in

1) 
  echo -e "Show All List\n"
  echo -e "ID\t Author Name \t Book Name \t Book ID \t Mobile Munber\t E-Mail \t Address \n"
  cat lib
  echo -e "\n";;
  
 
2)  
  echo "Enter Author ID:"
  read id
  echo "Enter Author Name: "
  read n
  echo "Enter Books Category: "
  read bk
  echo "Enter Books Title: "
  read bi
  echo "Enter Published Date: "
  read idt
  echo "Enter Mobile Number: "
  read mb
  echo "Enter E-Mail: "
  read ma
  echo "Enter Address"
  read ad
  echo  -e "Insert Complete Records\n "
  record="$id $n $bk $bi $idt $mb $ma $ad"
  echo $record>>lib
  echo -e "\n";;
 
 3)
   echo "Enter ID Number: "
   read id
   grep ^$id lib
   if [ $? -ne 0 ]; then
   echo "Record for this Id number does not exist."
   else
   grep -v $id lib>>rtmp
   cp rtmp lib
   echo -e "Deletion Complete."
   echo -e "\n"
   fi
   ;;
  
 4) 
   echo "Enter Id number: "
   read id1
  
   if  [ $? -ne 0 ]; then
   echo "Recored for ID numer dose not exist. "
   else 
   echo "Modify Author Id: "
   read id
   echo "Modify Author Name: "
   read n
   echo "Modify Book Name: "
   read bk
   echo "Modify Book Id: "
   read bi
   echo "Modify Published Date: "
   read idt
   echo "Modify Mobile Number: "
   read mb
   echo "Modify E-Mail: "
   read ma
   echo "Modify Address: "
   read ad
   echo -e "Modify Complete.\n"
   
   record="$id $n $bk $bi $idt $mb $ma $ad "
   var=`grep -n ^$id1 lib | cut -c 1`
   echo $var
   var1=`expr $var - 1`
   head -$var1 lib>mtemp
   echo $record>>mtemp 
   var3=`wc -l < lib` 
   var2=`expr $var3 - $var`
   tail -$var2 lib>>mtemp 
   cp mtemp lib
    fi
   echo -e "\n"
 ;;

5)
   echo " Enter ID Number of Author: "
   read id 
   echo -e "ID \t Author Name  \t Book Name \t Book Id \t Mobile Number \t E-Mail \t Address \n"
   grep ^$id lib
   echo -e "\n"
  ;;
  
 6) ;;
 * ) echo "Enter Right Choice." 
 esac
done
