# Part 1
**The faulty code that I will be using is the `static List<String> merge(List<String> list1, List<String> list2)` method.**
### Failure-inducing input for the buggy program
```
List<String> list1;  
List<String> list2;  
String SHOULD_BE_FIRST = "1";  
String SHOULD_BE_SECOND = "2";  
String SHOULD_BE_THIRD = "3";  
list1 = new ArrayList<String>();  
list2 = new ArrayList<String>();  
list1.add(SHOULD_BE_FIRST);  
list2.add(SHOULD_BE_SECOND);  
list2.add(SHOULD_BE_THIRD);  
List<String> list3 = ListExamples.merge(list1, list2);  
assertEquals(3, list3.size());
```
### Non-failure-inducing input for the buggy program
```
List<String> list1;  
List<String> list2;  
String SHOULD_BE_FIRST = "1";  
String SHOULD_BE_SECOND = "2";  
String SHOULD_BE_THIRD = "3";  
list1 = new ArrayList<String>();  
list2 = new ArrayList<String>();  
list1.add(SHOULD_BE_FIRST);  
list1.add(SHOULD_BE_SECOND);  
list2.add(SHOULD_BE_THIRD);  
List<String> list3 = ListExamples.merge(list1, list2);  
assertEquals(3, list3.size());
```
### Symptom caused by failure-inducing input
![image](https://github.com/thomas-rocha/cse15l-lab-reports/assets/156377384/6e9af232-1d6a-4132-aff7-b737ab012180)
An out of memory error.
### Output caused by non-failure-inducing input
![image](https://github.com/thomas-rocha/cse15l-lab-reports/assets/156377384/c10ced55-7e71-4e34-8790-8e5b67932e4d)
Tests successfully pass.

### Buggy code
```
static List<String> merge(List<String> list1, List<String> list2) {
    List<String> result = new ArrayList<>();
    int index1 = 0, index2 = 0;
    while(index1 < list1.size() && index2 < list2.size()) {
      if(list1.get(index1).compareTo(list2.get(index2)) < 0) {
        result.add(list1.get(index1));
        index1 += 1;
      }
      else {
        result.add(list2.get(index2));
        index2 += 1;
      }
    }
    while(index1 < list1.size()) {
      result.add(list1.get(index1));
      index1 += 1;
    }
    while(index2 < list2.size()) {
      result.add(list2.get(index2));
      index1 += 1;
    }
    return result;
  }
```
### Fixed code
```
static List<String> merge(List<String> list1, List<String> list2) {
    List<String> result = new ArrayList<>();
    int index1 = 0, index2 = 0;
    while(index1 < list1.size() && index2 < list2.size()) {
      if(list1.get(index1).compareTo(list2.get(index2)) < 0) {
        result.add(list1.get(index1));
        index1 += 1;
      }
      else {
        result.add(list2.get(index2));
        index2 += 1;
      }
    }
    while(index1 < list1.size()) {
      result.add(list1.get(index1));
      index1 += 1;
    }
    while(index2 < list2.size()) {
      result.add(list2.get(index2));
      index2 += 1;
    }
    return result;
  }
```
In the final while-loop, index1 is used instead of index2. 
This causes the loop to continuously add the element at 
index2 of list2 without ever breaking the loop. If this is 
changed to index2, then the loop will correctly run.

# Part 2
### Using -o
```
file . -name "chapter*" -o -name "Session*"
./technical/911report/chapter-1.txt
./technical/911report/chapter-10.txt
./technical/911report/chapter-11.txt
./technical/911report/chapter-12.txt
./technical/911report/chapter-13.1.txt
./technical/911report/chapter-13.2.txt
./technical/911report/chapter-13.3.txt
./technical/911report/chapter-13.4.txt
./technical/911report/chapter-13.5.txt
./technical/911report/chapter-2.txt
./technical/911report/chapter-3.txt
./technical/911report/chapter-5.txt
./technical/911report/chapter-6.txt
./technical/911report/chapter-7.txt
./technical/911report/chapter-8.txt
./technical/911report/chapter-9.txt
./technical/government/Alcohol_Problems/Session2-PDF.txt
./technical/government/Alcohol_Problems/Session3-PDF.txt
./technical/government/Alcohol_Problems/Session4-PDF.txt
```
```
$ find . -name "chapter*" -o -type d
.
./.git
./.git/hooks
./.git/info
./.git/logs
./.git/logs/refs
./.git/logs/refs/heads
./.git/logs/refs/remotes
./.git/logs/refs/remotes/origin
./.git/logs/refs/remotes/upstream
...
./technical/911report/chapter-1.txt
./technical/911report/chapter-10.txt
./technical/911report/chapter-11.txt
./technical/911report/chapter-12.txt
./technical/911report/chapter-13.1.txt
./technical/911report/chapter-13.2.txt
./technical/911report/chapter-13.3.txt
./technical/911report/chapter-13.4.txt
./technical/911report/chapter-13.5.txt
./technical/911report/chapter-2.txt
./technical/911report/chapter-3.txt
./technical/911report/chapter-5.txt
./technical/911report/chapter-6.txt
./technical/911report/chapter-7.txt
./technical/911report/chapter-8.txt
./technical/911report/chapter-9.txt
...
```
The -o option acts as an "or" operator and allows the find command to search for multiple things at once. This is useful to combine queries into one search.
Source: “Ultimate Guide to Linux Find Command.” SnapShooter, snapshooter.com/learn/linux/find#:~:text=%2Dtype%20%3A%20Used%20to%20specify%20the,belong%20to%20the%20specific%20group. Accessed 12 Feb. 2024. 
### Using -size
```
$ find . -type f -size 1k
./.git/COMMIT_EDITMSG
./.git/config
./.git/description
./.git/FETCH_HEAD
./.git/HEAD
./.git/hooks/applypatch-msg.sample
./.git/hooks/commit-msg.sample
./.git/hooks/post-update.sample
./.git/hooks/pre-applypatch.sample
./.git/hooks/pre-merge-commit.sample
./.git/hooks/pre-receive.sample
./.git/info/exclude
./.git/logs/HEAD
./.git/logs/refs/heads/main
./.git/logs/refs/remotes/origin/main
./.git/logs/refs/remotes/upstream/HEAD
./.git/logs/refs/remotes/upstream/main
./.git/objects/1a/992f62983421e2b7ca48da49f6eef713af240f
./.git/objects/1d/830b367fd4ea10466307132d62b5b2e1262415
./.git/objects/20/d013a56d25a519c6e3b02069240ce4d79b8eea
./.git/objects/25/1b7e66cd55518dc49ccf9260b0fc19ee07f210
./.git/objects/33/498d6f15258d82181513d7f6b6c40ac4d516cb
./.git/objects/35/c5d6f71e9b92b989be849a82f9d953e71ea7e0
./.git/objects/47/6d592862f96cb614ce011a4a5992ebd125ec65
./.git/objects/4c/943307e1f8e765ec52858bf7b0dd35f92981aa
./.git/objects/53/701335824771ed943d99e6891320e7303998f8
./.git/objects/5c/4bd315907cc8afb82cca631ff309992bf24fe7
./.git/objects/6f/2c6dddb512685bf8718c3186e23e5349abaa7b
./.git/objects/bf/3cf8559731453b50346e675eef5fe401c690ce
./.git/objects/c0/5995f1807bed0b9a3ea4a4080f42d4e1d615e2
./.git/objects/df/87e699fed9858da413603e34dea7e30085cf08
./.git/objects/f1/a99528b19e80d559badd328449881548359a4c
./.git/packed-refs
./.git/refs/heads/main
./.git/refs/remotes/origin/HEAD
./.git/refs/remotes/origin/main
./.git/refs/remotes/upstream/HEAD
./.git/refs/remotes/upstream/main
./count-txts.sh
./DocSearchServer.class
./README.md
./start.sh
```
```
$ find . -type f -size 2k
./.git/hooks/pre-commit.sample
./.git/hooks/pre-push.sample
./.git/hooks/prepare-commit-msg.sample
./.git/logs/refs/remotes/origin/HEAD
./.git/objects/5c/f6b482303db2d9640a7f86114c2c69999119b4
./.git/objects/cc/26552405f26e51a677a005ebb69525611d7fc3
./FileHelpers.class
./Server.class
./ServerHttpHandler.class
./technical/government/Media/Campaign_Pays.txt
./technical/government/Media/Court_Keeps_Judge_From.txt
./technical/government/Media/Fire_Victims_Sue.txt
./technical/government/Media/It_Pays_to_Know.txt
./technical/government/Media/Justice_requests.txt
./technical/government/Media/Lawyer_Web_Survey.txt
./technical/government/Media/Self-Help_Website.txt
./technical/plos/pmed.0020028.txt
./technical/plos/pmed.0020048.txt
./technical/plos/pmed.0020082.txt
./technical/plos/pmed.0020120.txt
./technical/plos/pmed.0020157.txt
./technical/plos/pmed.0020192.txt
```
The -size option allows the user to specify the size of the file in bytes to search for. This is useful if someone is trying to find which files are taking up the most space. 
Source: “Ultimate Guide to Linux Find Command.” SnapShooter, snapshooter.com/learn/linux/find#:~:text=%2Dtype%20%3A%20Used%20to%20specify%20the,belong%20to%20the%20specific%20group. Accessed 12 Feb. 2024. 
### Using the -not option
```
 find . -not -name "*.txt"
.
./.git
./.git/COMMIT_EDITMSG
./.git/config
./.git/description
./.git/FETCH_HEAD
./.git/HEAD
./.git/hooks
./.git/hooks/applypatch-msg.sample
./.git/hooks/commit-msg.sample
./.git/hooks/fsmonitor-watchman.sample
./.git/hooks/post-update.sample
./.git/hooks/pre-applypatch.sample
./.git/hooks/pre-commit.sample
./.git/hooks/pre-merge-commit.sample
./.git/hooks/pre-push.sample
./.git/hooks/pre-rebase.sample
./.git/hooks/pre-receive.sample
./.git/hooks/prepare-commit-msg.sample
./.git/hooks/push-to-checkout.sample
./.git/hooks/update.sample
./.git/index
./.git/info
./.git/info/exclude
./.git/logs
./.git/logs/HEAD
./.git/logs/refs
./.git/logs/refs/heads
./.git/logs/refs/heads/main
./.git/logs/refs/remotes
./.git/logs/refs/remotes/origin
./.git/logs/refs/remotes/origin/HEAD
./.git/logs/refs/remotes/origin/main
./.git/logs/refs/remotes/upstream
./.git/logs/refs/remotes/upstream/HEAD
./.git/logs/refs/remotes/upstream/main
./.git/objects
./.git/objects/13
./.git/objects/13/d40c6b3d22431d1aac51dce2f7b93fafd0ab45
./.git/objects/1a
./.git/objects/1a/992f62983421e2b7ca48da49f6eef713af240f
./.git/objects/1d
./.git/objects/1d/830b367fd4ea10466307132d62b5b2e1262415
./.git/objects/20
./.git/objects/20/affbf8a1b24bec98f81cfe678d9db8a0b654d9
./.git/objects/20/d013a56d25a519c6e3b02069240ce4d79b8eea
./.git/objects/25
./.git/objects/25/1b7e66cd55518dc49ccf9260b0fc19ee07f210
./.git/objects/33
./.git/objects/33/498d6f15258d82181513d7f6b6c40ac4d516cb
./.git/objects/35
./.git/objects/35/c5d6f71e9b92b989be849a82f9d953e71ea7e0
./.git/objects/47
./.git/objects/47/6d592862f96cb614ce011a4a5992ebd125ec65
./.git/objects/4c
./.git/objects/4c/943307e1f8e765ec52858bf7b0dd35f92981aa
./.git/objects/53
./.git/objects/53/701335824771ed943d99e6891320e7303998f8
./.git/objects/5c
./.git/objects/5c/4bd315907cc8afb82cca631ff309992bf24fe7
./.git/objects/5c/f6b482303db2d9640a7f86114c2c69999119b4
./.git/objects/6f
./.git/objects/6f/2c6dddb512685bf8718c3186e23e5349abaa7b
./.git/objects/bf
./.git/objects/bf/3cf8559731453b50346e675eef5fe401c690ce
./.git/objects/c0
./.git/objects/c0/5995f1807bed0b9a3ea4a4080f42d4e1d615e2
./.git/objects/cc
./.git/objects/cc/26552405f26e51a677a005ebb69525611d7fc3
./.git/objects/df
./.git/objects/df/87e699fed9858da413603e34dea7e30085cf08
./.git/objects/e9
./.git/objects/e9/4a693653d333df90b9a4bcd0a5ef8b1779c910
./.git/objects/f1
./.git/objects/f1/a99528b19e80d559badd328449881548359a4c
./.git/objects/info
./.git/objects/pack
./.git/objects/pack/pack-f3e64844a2bd252cbb7d4b547cb60beb349fd441.idx
./.git/objects/pack/pack-f3e64844a2bd252cbb7d4b547cb60beb349fd441.pack
./.git/packed-refs
./.git/refs
./.git/refs/heads
./.git/refs/heads/main
./.git/refs/remotes
./.git/refs/remotes/origin
./.git/refs/remotes/origin/HEAD
./.git/refs/remotes/origin/main
./.git/refs/remotes/upstream
./.git/refs/remotes/upstream/HEAD
./.git/refs/remotes/upstream/main
./.git/refs/tags
./count-txts.sh
./DocSearchServer.class
./DocSearchServer.java
./FileHelpers.class
./Handler.class
./lib
./lib/hamcrest-core-1.3.jar
./lib/junit-4.13.2.jar
./README.md
./Server.class
./Server.java
./ServerHttpHandler.class
./start.sh
./technical
./technical/911report
./technical/biomed
./technical/government
./technical/government/About_LSC
./technical/government/Alcohol_Problems
./technical/government/Env_Prot_Agen
./technical/government/Gen_Account_Office
./technical/government/Media
./technical/government/Post_Rate_Comm
./technical/plos
./test-files
./test-files/test1.txt.expect
./test.sh
./TestDocSearch.java
./URLHandler.class
```
```
$ find . -not -type f
.
./.git
./.git/hooks
./.git/info
./.git/logs
./.git/logs/refs
./.git/logs/refs/heads
./.git/logs/refs/remotes
./.git/logs/refs/remotes/origin
./.git/logs/refs/remotes/upstream
./.git/objects
./.git/objects/13
./.git/objects/1a
./.git/objects/1d
./.git/objects/20
./.git/objects/25
./.git/objects/33
./.git/objects/35
./.git/objects/47
./.git/objects/4c
./.git/objects/53
./.git/objects/5c
./.git/objects/6f
./.git/objects/bf
./.git/objects/c0
./.git/objects/cc
./.git/objects/df
./.git/objects/e9
./.git/objects/f1
./.git/objects/info
./.git/objects/pack
./.git/refs
./.git/refs/heads
./.git/refs/remotes
./.git/refs/remotes/origin
./.git/refs/remotes/upstream
./.git/refs/tags
./lib
./technical
./technical/911report
./technical/biomed
./technical/government
./technical/government/About_LSC
./technical/government/Alcohol_Problems
./technical/government/Env_Prot_Agen
./technical/government/Gen_Account_Office
./technical/government/Media
./technical/government/Post_Rate_Comm
./technical/plos
./test-files
```
The -not option returns all but the following search query. This is useful if there is one specific thing that the user does not want to look for. 
Source: “Ultimate Guide to Linux Find Command.” SnapShooter, snapshooter.com/learn/linux/find#:~:text=%2Dtype%20%3A%20Used%20to%20specify%20the,belong%20to%20the%20specific%20group. Accessed 12 Feb. 2024. 
### Using the -empty option
```
$ find . -type f -empty

```
```
$ find ./technical/911report/ -type f -not -empty
./technical/911report/chapter-1.txt
./technical/911report/chapter-10.txt
./technical/911report/chapter-11.txt
./technical/911report/chapter-12.txt
./technical/911report/chapter-13.1.txt
./technical/911report/chapter-13.2.txt
./technical/911report/chapter-13.3.txt
./technical/911report/chapter-13.4.txt
./technical/911report/chapter-13.5.txt
./technical/911report/chapter-2.txt
./technical/911report/chapter-3.txt
./technical/911report/chapter-5.txt
./technical/911report/chapter-6.txt
./technical/911report/chapter-7.txt
./technical/911report/chapter-8.txt
./technical/911report/chapter-9.txt
./technical/911report/preface.txt
```
The -empty option looks for empty files and directories, depending on what is specified by -type. This is useful to find files that aren't in use.
Source: “Ultimate Guide to Linux Find Command.” SnapShooter, snapshooter.com/learn/linux/find#:~:text=%2Dtype%20%3A%20Used%20to%20specify%20the,belong%20to%20the%20specific%20group. Accessed 12 Feb. 2024. 

