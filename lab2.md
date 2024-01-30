# ChatServer code:
![image](https://github.com/thomas-rocha/cse15l-lab-reports/assets/156377384/2ae21cfe-35aa-43b4-9acd-fd533c5870d1)

## Code Screenshot 1:
![image](https://github.com/thomas-rocha/cse15l-lab-reports/assets/156377384/6149d0b1-14bb-44c5-86b2-a9e8f1467c94)
The method `handleRequest(URI url)` is used in this screenshot. The argument for the method was the url that was updated.vThe `parameters[]` array was updated to include the message portion of the path in index 0 and the user portion in index 1. Index 0 became `"s=Hello!"` and index 1 became `"user=thomas"`. The `messages[]` and ` user[]` arrays were both updated to separate the username and message from their identifiers (`"user="` for example). The values became `"s"` and `"Hello!"` for `messages[]` and `"user"` and `"thomas"` for `user[]`. The string `messages` is then updated with the correct username and message from the corresponding arrays to become `"thomas: Hello!\n"`.

## Code Screenshot 2:
![image](https://github.com/thomas-rocha/cse15l-lab-reports/assets/156377384/1db65427-da85-4750-b245-65cbcc7f9848)
The method `handleRequest(URI url)` is used in this screenshot. The argument for the method was the url that was updated. The `parameters[]` array was updated to include the message portion of the path in index 0 and the user portion in index 1. Index 0 became `"s=Howdy"` and index 1 became `"user=other_user"`. The `messages[]` and ` user[]` arrays were both updated to separate the username and message from their identifiers. The values became `"s"` and `"Howdy"` for `messages[]` and `"user"` and `"other_user"` for `user[]`. The string `messages` is then updated to add the new values to the pre-existing string to become `"thomas: Hello!\other_user: Howdy\n"`.

## ieng6 Public and Private Keys
![image](https://github.com/thomas-rocha/cse15l-lab-reports/assets/156377384/f9460336-9a62-432d-b70d-d4512a512df9)

## No password needed to log in to ieng6 machine
![image](https://github.com/thomas-rocha/cse15l-lab-reports/assets/156377384/32b4a866-b5d8-46bb-9004-441b1959cb2d)

In this lab, I learned about authorization keys and the `mkdir` and `scp` commands, as well as how to look up the functionality of commands using the `man` command. I also learned that multiple people can access the same web server and update a virtual machine at the same time. 
