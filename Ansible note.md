[toc]

# **C**loud **N**ative **S**ervice是甚麼?
CNS是一種經過雲原生設計的服務或應用程式，這種服務能夠充分發揮雲計算的彈性、可擴展性和可靠性。

雲原生應用程式通常使用容器化技術（例如 Docker）來封裝應用程式和其相依的環境，並使用容器管理平台（例如 Kubernetes）來自動化部署、擴展和管理這些容器。雲原生還鼓勵使用微服務架構，將應用程式拆分成小型、獨立的服務，以實現更高的靈活性和可維護性。

總的來說，Cloud Native Service 是指符合雲原生設計理念和標準的服務或應用程式，這些服務能夠充分利用雲計算的優勢，提供更好的效能。



# DevOps
## What
DevOps = **Dev**lopment(開發) + **Op**eration**s**(維運)是一套開發方法論，主要目的是要讓開發流程能更快更有效率，並讓開發者跟維運人員能好好合作。

## Why
在這個Time to Market的時代，團隊需要分工，而DevOps的存在目的在於時刻提醒「開發多去想維運面，維運多去想開發面。」，才能兼顧速度與品質。

## How
1. 開發端及維運端都需花時間為對方著想，ex.在開發程式時註解清楚以方便在有運行有問題時方便做修正。
2. 增強學習 :  DevOps 為了要做到互助合作，解決不必要的衝突，勢必得學習其他專業，來了解衝突是如何發生，並考慮更多角度來想出更好的方法。
3. 自動化 

# Docker
## What
Docker是一個開源的容器化平台，用於創建、部署和運行輕量且可攜帶的容器。每個容器都包含一個應用程式及其相依的環境，如程式碼、執行環境、函式庫、設定檔等。

Docker 技術的核心概念是容器化。Container是一種輕量且獨立的虛擬化單元，它們可以在任何支援 Docker 的環境中運行，如開發人員的本機電腦、測試伺服器或雲端主機。

## 對DevOps的幫助
Docker透過Dockerfile來記錄建立Container映象檔的每一個步驟，可以將建立應用程式執行環境的過程和配置參數，完整地記錄下來。開發人員和維運人員之間可以利用Dockerfile來溝通對執行環境的討論。甚至結合版本控制服務如GitHub，可以讓Dockerfile具備版本控制功能，能將基礎架構程式化（Infrastructure as code）來管理。

## Container vs Virtual Machine(VM)
![](https://phoenixnap.com/kb/wp-content/uploads/2021/04/container-vs-virtual-machine.png)
### Container
1. 技術層次 : 它在作業系統層次上進行虛擬化。Container共享主機作業系統的核心，但是具有自己的獨立文件系統、環境變數和進程空間。
2. 資源需求 : 共享主機的OS -> 佔用較少的記憶體和硬體資源。在相同的硬體上，可以運行比VM更多的Container。
3. 運行速度 : 容器在共享主機作業系統的情況下運行 -> 啟動和運行速度較快。
4. 隔離性：較弱，因為它們共享主機OS的核心。這意味著Container之間可能更容易發生資源衝突或安全問題。
### VM
1. 技術層次 : 它在物理硬體上模擬一個完整的虛擬環境，包括虛擬的作業系統、硬體資源（如 CPU、記憶體和網路介面）和磁碟空間。
2. 資源需求 : 每個VM皆須模擬完整硬體及OS -> 在運行多個虛擬機器時，需要較多的記憶體和硬體資源。
3. 運行速度 : 由於VM模擬了整個作業系統 -> 啟動和運行速度較慢。
4. 隔離性：提供較高的隔離性，因為每個VM都運行在獨立的虛擬環境中。

# Ansible
## What
是一種IT自動化工具可以讓系統配置以及應用軟體部署達到自動化
用於遠端配置管理
編排高階IT mission
using Python

## Why
藉由流程標準化、自動化、單元化來減少錯誤及成本的產生

## Ansible的特性與控制
![](https://hackmd.io/_uploads/r18S40Q53.png)

 :arrow_up_small: 因為Linux系統中皆有默認安裝SSH Protocol，因此我們可以基於SSH remote control，無須代理就能控制遠端的主機。

## Ansible的使用結構

![](https://hackmd.io/_uploads/ByHSSAQ92.png)

 :arrow_up_small: 一個PlayBook中存在多個Roles以對應不同的Task
 
## Ansible的其他特性

### 三個重要模組 : 
#### Paramiko : SSH遠端管理模組
#### PyYAML : PlayBook的開發格式
#### Jinja2 : 樣板處理器

### 冪等性 : PlayBook執行一次跟執行多次得效果一樣(系統會判斷若文件已存在此指令 -> Skip)

### 相容性 : 不支援Windows作為Controller(使用Linux)

## Ansible架構圖
![](https://hackmd.io/_uploads/ryNitRX9h.jpg)
<br/>
![](https://hackmd.io/_uploads/r1H1cA7qn.jpg)

## Ansible環境建置
![](https://hackmd.io/_uploads/HJScsCQch.jpg)
### Step0
#### Install VSCode
+ Install  Plugin
  - Ansible:檢查Ansible語法、程式碼提示
  - YAML:檢查YAML語法
  - SFTP:遠端傳輸文件
  - Jinja:模板引擎格式檢查器
  
+ Write sample file
在VSCode中創資料夾裡面放個txt檔作為測試

+ Use SFTP to transfer file
  - 產出設定檔: Press Shift + Ctrl + P -> sftp:config
```
  name:自訂義
  host:要上傳的主機位址 (去control node下輸入ifconfig找到IP)
  username:root
  remotePath:/root
```
  改完後在左邊列表處右鍵 Local->Remote 輸入密碼就成功傳送了
  驗證
  
  ### 需用到的linux語法
  `rm -rf` /資料夾地址 : 刪除整個資料夾
  `df` : 查看空間使用狀況
    * cd : 回使用者目錄
  `cd /usr/bin` : 到/usr/bin這個目錄
  `cd ..` : 回上一層
  `cd eugene/` : 到eugene這個目錄
  
    * pwd : 顯示目前所在目錄

    * ls : 取得當前資料夾及檔案名稱
以行的方式成列： -l
顯示隱藏檔案： -a
按照檔案大小排序： -S
反向排序： -r
按照修改時間排序： -t
可依需求調整參數
 ex.
 `ls -la`
 ls -
    * grep : 依關鍵字找出想要的資料
    ex.
    ls | grep eugene (可找到名為eugene的檔案)
    * cat : 將檔案內容列出
    ex.
    cat Lesson1/sample.txt
    * 使用模組 
    ex.
    ansible <目標主機或主機組> -m <模塊名稱> : "-m"告訴 Ansible 要在目標主機上運行哪個模塊。
### Step1
#### 配置ansible.cfg

##### What
在 Ansible 中，我們可以透過配置 Ansible 的組態檔案 - ansible.cfg，來指定 Ansible 要去哪裡查找 role 的路徑。

創建.cfg檔在資料夾中
```linux
[defaults]
inventory = ./hosts  (主機清單)
host_key_checking = False (檢查被連線主機的公鑰是否存在在已知金鑰中)
private_key_file = 路徑/id_rsa (告訴Ansible金鑰在哪)
(cd .ssh/ -> ls -la -> pwd -> 複製此路徑給private_key_file)
log_path = ./log/ansible.log (指定Log輸出位置)
```

在左邊列表處右鍵 Local->Remote
驗證

### Step2
#### 設置hosts主機清單
創建hosts在資料夾中

```
[node(自訂義)]
ansible-node
XXXXXX ansible_user = root
(cat /etc/hosts or IP放入XXXXXX)
```
在左邊列表處右鍵 Local->Remote

### Step3
#### 使用Ping模組
##### 對所有主機使用Ping模組
`ansible all -m ping`
(ansible <目標主機或主機組> -m <模塊名稱> : 告訴 Ansible 要在目標主機上運行哪個模塊。)
##### 對主機群組使用Ping模組
`ansible DynasafeVM -m ping`

#### 使用Command模組
`ansible all -m command -a "echo Hello World"`
("-a" 後面跟著要傳遞给 "command" 模塊的命令。)
(echo = cout的概念)

## 若使用SFTP傳輸時，不想每次都輸入密碼
### Step0
Copy上面的步驟到新的資料夾

### Step1
打開terminal輸入 
```
ssh-keygen (產生Key)
cd .ssh (到ssh)
ls (列出來檢查key是否已產生)
type ~/.ssh/id_rsa.pub| ssh dynasafe@10.240.216.188 "cat >> ~/.ssh/authorized_keys" (將Key分享給control node)
密碼 : esun@1313
```

驗證
`ssh dynasafe@10.240.216.188` (不須密碼了)

### Step2
修改SFTP設定檔

```
name : (不動)
host : 10.240.216.188 (control node IP)
protocol : sftp
port : 22
username : dynasafe
remotePath : /home/dynasafe/
privateKeyPath : (上面Key產出的位址)
uploadOnSave : true
```

在左邊列表處右鍵 Local->Remote

驗證
`ls` (家目錄底下會有dynasafe的folder)

## Ansible常見指令
+ ansible : 使用ansible功能 (執行Ad-Hoc)
  - `ansible --version` (顯示版本)
  - `ansible all --list-hosts` (顯示主機列表)
  - `ansible all -m ping` (執行Ad-Hoc)

+ ansible Ad-Hoc
`ansible <主機> -m<Module> -a<Module Params>`
  - -k (提示輸入Managed Node密碼(不建議))
  - -K (提示輸入Managed Node root密碼)
  - -i (指定執行的主機清單(inventory))
  - -v (顯示更詳細的執行資訊)
  - -b (使用sudo執行命令)
  - -limit (限定執行的主機清單)
  
  1. Ping (Ping Managed Node)
  ex. `ansible all -m ping` 
  
  2. command (在Managed Node執行指令)
  ex. 
 ` ansible all -m command -a "echo Hi" `(讓Managed node回傳Hi)
  `ansible all -m command -a "ls -la"` (讓Managed node列出目錄底下所有檔案)
  
  3. user (在Managed node創建使用者)
  ex. `ansible all -m user -a "name=< NAME > password=< HASH PASSWORD >"`
  + 產出Hash paassword的方法
`ansible all -m debug \ -a "msg={{ 'mypassword'|password_hash('sha512', 'XXXX') }}"`
 
  4. group (在Managed node設定group)
  ex.
  `ansible all -m group -a "name=mygroup state=pressent"` (創建用戶group)
`ansible all -m group -a "name=mygroup state=abseent"` (刪除用戶group)
  `ansible all -m group -a "name=mygroup state=present gid=1001"` (修改用戶group)
 
  5. copy (將指定文件複製到Managed code的指定位置)
  ex.` ansible all -m copy -a "src=/path/to/local/file dest=/path/on/remote"`
  + 參數
    1. src : 本地的文件或是目錄
    2. dest : 遠程的目錄
    3. mode : 賦予檔案的權限(ex:722)
    4. directory_mode : 賦予目錄的權限
    5. owner : 賦予擁有者
    6. group : 賦予擁有者群組
    
 ## Ansible Ad-Hoc - copy
 ### ex1. 將以自己{英文名}的文件複製到Managed node的家目錄底下
 + Step0
 在Lesson2下創建一個檔名為英文名的檔案
 在左邊列表處右鍵 Local->Remote
 
 + Step1
 使用copy module將此檔案複製到Managed node的家目錄底下(權限為770)
` ansible all -m copy -a "src=./eugene dest=/home/dynasafe/ mode=770"`
 
 ### ex2. 將以自己{英文名}_folder的資料夾複製到Managed node的家目錄底下
 + Step0
 在Lesson2下創建一個檔名為{英文名}_folder的資料夾
 並把eugene的檔案丟進此資料夾
 
 在左邊列表處右鍵 Local->Remote
 + Step1
 使用copy module將此目錄複製到Managed node的家目錄底下(權限為770)
```
 ansible all -m copy -a "src=./eugene_folder dest=/home/dynasafe/ directory_mode=770"
```
 
 6. file (對Managed node執行各種文件的操作)
 ex.` ansible all -m file -a ""`
    + 功能
      1. path : 文件 / 目錄 位置
      2. state
         - absent : 遞歸刪除文件
         - touch : 創建文件
         - directory : 創建目錄 (如果中間的目錄不存在會一併創建)
         - file : 修改「已存在」檔案(搭配其他參數使用 像mode)
         - hard : 修改或創建 Hard Link
         - link : 修改或創建 Symbolic Link
      3. mode: 權限
      4. recurce : 是否要遞歸 (通常搭配修改目錄下檔案權限)
 ## Ansible Ad-Hoc - file
### ex1 在Managed node創建一個資料夾在使用者目錄下 (命名 : {英文名}_file_module)
 
 `ansible all -m file -a "path=/home/dynasafe/eugene_folder_module state=directory"`
  
 顯示"changed": true -> 成功
 
### ex2 在上面創建的資料夾下({英文名}_file_module)，創建一個檔案(命名:{英文名})並且權限賦予666

 `ansible all -m file -a "path=/home/dynasafe/eugene_folder/eugene state=touch mode=666"`
 
 顯示"changed": true -> 成功
 
### ex3 刪除剛剛創建的資料夾({英文名}_file_module)

 `ansible all -m file -a "path=/home/dynasafe/eugene_folder_module/eugene state=absent"`
 
 顯示"changed": true -> 成功
 
 7. gather_facts : 取得Managed node詳細資訊
 ex. 
 `ansible all -m gather_facts`
 `ansible all -m gather_facts --tree ./` (將主機詳細資料處存到資料夾底下)
 
 8. yum : 在Managed node執行yum模組
 ex. 
 `ansible all -m yum -a ""`
 `ansible all -m yum -a "name=httpd state=present"` (安裝httpd)
    + 參數
      1. name : Package名稱
      2. state 
         - absent : 移除package
         - pressent : 檢查package是否存在，若不在就安裝
         - latest : 安裝最新版的package
      3. update_cache : 是否更新快取
      4. disable_gpg_check : 是否禁用檢查GPG Key
      5. conf_file : 指定yum repo位置
      
 9. service : 在Managed node上操作service
 ex.
 `ansible all -m service -a ""`
 `ansible all -m service -a "name=httpd state=started"` (啟動httpd服務)
 
    + 參數
      1. name : service名稱
      2. state
         - started : 啟動服務
         - stopped : 暫停服務
         - reloaded : 重新加載服務
         - restarted : 重啟服務
      3. enabled : 在開機後，自動啟動
      
 10. seport : 在Managed node設定SELinux
 ex. 

`ansible all -m seport -a ""`
 `ansible all -m seport -a "ports=8080 proto=tcp setype=http_port_t state=present"`
     + 參數
       1. ports : Ports (可以多個 / 區間)
       2. setype : SELinux類型
       3. proto : 協議
          - tcp
          - udp
       4. state
          - present : 添加
          - absent : 棄用
          
 11. reboot : 重啟Managed node
 ex.
 `ansible all -m reboot -b`
      
      
+ ansible-doc : 查看ansible module文件
  - `ansible-doc yum` (查看yum module文件)

+ ansible-playbook : 執行ansible腳本
  - `ansible-playbook -i INVENTORY.ini <playbook_file>` (指定主機清單文件)
  - `ansible-playbook -e "var=value" <playbook_file>` (帶變數)
  - `ansible-playbook --become <playbook_file>` (使用sudo權限)

+ ansible-vault : 加密
  - `ansible-vault creat testVault.yml` (創建)
  - `ansible-vault view testVault.yml` (閱覽)
  - `ansible-vault edit testVault.yml` (編輯)
  - `ansible-vault decrypt testVault.yml` (解密)
  - `ansible-vault encrypt testVault.yml` (加密已存在檔案)

+ ansible-galaxy : 到ansible平台搜尋、下載可用的role
  - `ansible-galaxy search <role_name>` (搜尋)
  - `ansible-galaxy install <role_name>` (下載)
  - `ansible-galaxy list` (列出已下載角色)
  - `ansible-galaxy remove` <role_name> (移除)
  
## Group_vars & Host_vars (定義主機群組變數)
  
  ![](https://hackmd.io/_uploads/rJ8rCIL52.png)
  
  ### Step0 (建立Group_vars)
  在Lesson2資料夾下創group_vars folder
  在裡面創一個 主機名稱.yml檔 (ManagedNode.yml)
  裡面輸入 group_var: aaa
  
  在左邊列表處右鍵 Local->Remote
  
  驗證
  ls group_vars/
  
  ### Step1
  使用Debug Module將變數print出來
  `ansible all -m debug -a "msg={{ group_var }}"`
  
  ### Step2 (建立Host_vars)
  在Lesson2資料夾下創host_vars folder
  ***hosts內的ip需改成主機名稱***
  在裡面創一個 主機名稱.yml檔 (pubauto02t.yml)
  裡面輸入 host_var: 123
  
  在左邊列表處右鍵 Local->Remote
  
  ### Step3
  使用Debug Module將變數print出來
  `ansible all -m debug -a "msg={{ host_var }}"`
  
  ### 若在group_vars與host_vars定義了相同變數?
  因為 Host > Group 所以只會顯示出host_vars的內容
  
  ## 加密host_vars內的文件
  `cd host_vars/` (進去)
  `ls` (看裡面有啥)
  `ansible-vault encrypt pubauto.yml` (加密)
  
  若直接cat會出現亂碼(因為加密了)
  
  ## 閱覽加密文件
  `cd host_vars/`
  `ansible-vault view pubauto02t.yml`
  輸入密碼
  
  ## 編輯加密文件
  `ansible-vault edit pubauto02t.yml`
  輸入密碼
  
  Click i
  可開始做更改
  
  Click esc (保存退出)
  Type wq
  
  ## 顯示加密文件內的變數value
`  ansible all -m debug -a "msg={{ host_var }}" --ask-vault-pass`
  
  ## 解密文件
  `ansible-vault decrypt pubauto02t.yml`
   
  ## YAML
  ### What 
  可讀性最高的Data Format，另外常見的有(XML,JSON...)
  
  ### Basic Format
  ![](https://hackmd.io/_uploads/rJklCwLc2.png)

## 撰寫Play
![](https://hackmd.io/_uploads/rkViwPDqh.png)


  ### ex1 撰寫一個Play，並符合以下條件
  + 須至少包含一個Task
  + 將Managed node的ansible_date_time印出來

#### Step0 
先創一個Lesson3 folder
把之前的cfg檔、hosts folder複製進來(cfg檔要改./hosts)

上傳到遠端

驗證
`ansible all -m ping`

#### Step1
創建first-practice.yml檔

---
```
-name: First practice
 hosts: node
 remote_user: dynasafe
 gather_facts: true (是否需要取得主機清單的詳細資訊，true才能知道ansible_date_time)
 
 tasks:
 -name: Print time
 ansible.builtin.debug:
  msg: "{{ ansible_date_time }}"
```
  
 上傳 
 
 驗證
 ```
ls -la
 ansible-playbook first-practice.yml
```

## Var

### Variable規範
+ 只能包含數字、字母、下劃線
+ 不能包含Python關鍵字
+ 不能包含Playbook關鍵字
+ 不能以數字開頭

### Variable定義
![](https://hackmd.io/_uploads/H1Rf9vvch.png)

### ex1 撰寫一個Playbook，並符合以下條件
+ 在Play中定義變數，並且印出來
+ 將變數宣告在外部檔案並引入Play，並且印出來
+ 在group_vars、host_vars、外部變數檔、Play中定義變數，並了解變數優先級
+ 撰寫兩個外部變數檔，並宣告相同變數，辨別其優先級

#### Step0
創一個var-practice.yml檔

```
---
-name: Var practice
 hosts: node
 remote_user: dynasafe
 gather_facts: false
 vars:
  key1: value1
 
 task:
  -name: Print Var
  ansible.builtin.debug:
  msg: "{{ key1 }}"
```

 上傳
 
 驗證
 ```
ls -la
 ansible-playbook var-practice.yml
```
 
 #### Step1
 創一個vars folder
 裡面創一個main.yml檔
 `var_file: The var from file`

 在var-practice.yml下方加入
 
```
 -name: Var File
 hosts: node
 remote_user: dynasafe
 gather_facts: false
 vars_files:
  -./vars/main.yml
 
 task:
  -name: Print Var
  ansible.builtin.debug:
  msg: "{{ var_file }}"
```
  
  上傳
  
  驗證
  `ansible-playbook var-practice.yml`
  
  #### Step2
  優先順序 : 外部變數檔 > Playbook > Host > Group 
  
  #### Step3
  在vars folder中再創建一個main2.yml
  改裡面內容
  引入
 ```
 vars_files:
  -./vars/main.yml
  -./vars/main2.yml
```
  
-> 顯示main2的
-> 後引入的變數檔案會覆蓋先引入的

優先順序 : 後導入 > 先導入 > Playbook > Host > Group 

## Ansible Lint
+ 分析是否符合Ansible規範格式
+ 達到撰寫風格統一

### Install
+ Install pip3
 `sudo yum install python3-pip`
 
+ Install ansible-int
 `sudo pip3 install ansible-lint`

### Use
`ansible-lint <YAML File>`

`ansible-lint *.yml` (檢查當前目錄下的所有yml)

## Ansible Best Practice

![](https://hackmd.io/_uploads/HJicTdDqn.png)


### Why
針對不同環境，會有不同的變數設置

### How
+ 創建inventories資料夾
+ 再依照環境不同，在inventories內做資料夾的創建

### ex1 創建inventories資料夾，並實作以下步驟
+ 在inventories資料夾中，創建兩種環境的主機清單(test / production)
+ 在test / production內的主機群組變數中設置相同key的變數
+ 在playbook中，使用debug模組將變數印出來
+ 在ansible.cfg藉由引用不同的inventory來做切換

#### Step0
在Lesson3底下創建inventories folder
底下再創建production及test folder
把hosts、host_vars、group_vars拖曳到這兩個folder中
把group_vars裡的node.yml檔內容改成 
```
var_file: the var from (test or prod) env
```

#### Step1
刪除以下(因為已分別移到prod跟test folder 中了)

```
rm -rf ./group_vars/
rm -rf ./host_vars/
rm -rf hosts
```

驗證
```
ls -la
cd inventories/
ls -la
```
#### step2
創建inventories-practice.yml

```
---
-name: Inventories Practice
 hosts: node
 remote_user: dynasafe
 gather_facts: false
 
 tasks:
  -name: Print env var
  ansible.builtin.debug:
   msg: "{{ var_file }}"
```
#### step3
更改ansible.cfg中的inventory
`inventory = ./inventories/production/`
`inventory = ./inventories/test/`

驗證

`ansible-playbook ./inventories-practice.yml`

## Ansible function

### 迴圈
 #### Loop-迴圈
 ##### 陣列
 ![](https://hackmd.io/_uploads/BJplSjwc2.png)
```
ansible.builtin.debug:
 msg: "{{ item }}"
 loop: "{{ key1 }}"
```
 ##### 物件項目的陣列
![](https://hackmd.io/_uploads/rJZqriv53.png)
```
ansible.builtin.debug:
 msg: "{{ item.name }} is {{ item.gender }}"
 loop: "{{ classmate }}"
```
##### 物件
![](https://hackmd.io/_uploads/BJrtUjD92.png)
```
ansible.builtin.debug:
 : "{{ item.key }} = {{ item.value }}"
 loop: "{{key1 | dict2items }}"
```

 - Loop-雙重迴圈
![](https://hackmd.io/_uploads/HJLQvsPq2.png)
```
ansible.builtin.debug:
 msg: "{{ item }}"
 loop: "{{ classmate | product(gender) | list }}"
```
 
 - Loop-攤平項目
![](https://hackmd.io/_uploads/ry0FvoDch.png)
```
ansible.builtin.debug:
 var: item
 loop: "{{ key1 | flatten }}"
```

 - Loop-取得迴圈資訊
  1. 增加Loop option
 
```
loop: "{{ key1 }}"
   loop_control:
   extended: true
```

   2. 選擇你要的迴圈資訊
![](https://hackmd.io/_uploads/rkyBZ2Pqh.png)



### ex1 定義一個變數key1，value類形是包含長度三的陣列。請依序列印陣列的項目

創建loop-prac.yml在Lesson3中
```
---
-name: First loop
 hosts: node
 remote_user: dynasafe
 gather_facts: false
 
 vars:
  key1: [1, 2, 3]

tasks:
 -name: Print item From Array
  ansible.builtin.debug:
   msg: "{{ item }}"
   loop: "{{ key1 }}"
```

上傳

驗證
```
ls -la
ansible-playbook loop-prac.yml
```

### ex2 定義兩個變數。使用雙重迴圈的方式，列出所有排列組合併印出(需要顯示項次)
#### Step0
```
---
-name: Second loop
 hosts: node
 remote_user: dynasafe
 gather_facts: false
 
 vars:
  key1: [1, 2, 3]
  key2: [a, b, c]
tasks:
 -name: Second loop
  ansible.builtin.debug:
   msg: "{{ item }} - {{ ansible_loop.index0 }}"
   loop: "{{ key1 | product(key2)  | list }}"
   loop control:
    extended: true
```

上傳

驗證
```
ls -la
ansible-playbook loop-prac.yml
```

### ex3 將此陣列攤平並列印
![](https://hackmd.io/_uploads/B1ptfhw9h.png)
```
---
-name: Play3
 hosts: node
 remote_user: dynasafe
 gather_facts: false
 
 vars:
  key1:
   -value1
   -[value2, value3]
   
 tasks:
  -name: Flatten Array
   ansible.builtin.debug:
   msg: "{{ item }}"
   loop: "{{ key1 | flatten}}"
```
上傳

驗證
```
ls -la
ansible-playbook loop-prac.yml
```
### ex4 用此變數列印出此訊息(<name>is<gender>)
![](https://hackmd.io/_uploads/S1Z7mhv53.png)
```
---
-name: Play4
 hosts: node
 remote_user: dynasafe
 gather_facts: false
 
 vars:
  classmate:
   -{ name: Kate, gender: female}
   -{ name: Kevin, gender: male}
   
   
 tasks:
  -name: Flatten Array
   ansible.builtin.debug:
   msg: "{{ item.name }} is{{ item.gender }}"
   loop: "{{ classmate }}"
```
上傳

驗證
```
ls -la
ansible-playbook loop-prac.yml
```

### 判斷
 - conditionals in Loop (迴圈內做判斷)
    - ex.只列出大於3的項目
    

```
-name: When function
 hosts: DynasafeRockyLinux
 remote_user: dynasafe
 gather_facts: false
 vars: 
 key1: [1, 2, 3, 4, 5, 6]
    
tasks: 
 name: Print item bigger than 3
  ansible.builtin.debug:
   msg: "{{ item }}"
 loop: "{{ key1 }}" 
 when: item > 3
```


    
 - Conditionals based on ansible_facts (根據主機資訊判斷
    - ex.若系統為Rocky，就執行此task
    
```
ansible.builtin.debug:
     msg: "Rocky execution"
    when: ansible_facts['distribution'] == 'Rocky'
```

    
 - Conditionals based on registered variables (把執行結果註冊起來，根據結果決定是否要執行第二個task) 
result 可能為 succeeded / failed / skipped
```
tasks:
     -name: Echo
      ansible.builtin.command: echo "Hello"
      register: result
    
     -name: Task2
      ansible.builtin.debug:
      var: result
      when: result is succeeded
```

### ex1 1~10的陣列變數，只列印出大於6的item
    
創建when-prac.yml在Lesson3中
```
---    
-name: Play1
     hosts: node
     remote_user: dynasafe
     gather_facts: false
     vars: 
      key1: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    
    tasks: 
     -name: Print value bigger than six
      ansible.builtin.debug:
       msg: "{{ item }}"
       loop: "{{ key1 }}" 
       when: item > 6
```
上傳

驗證
```
ansible-playbook when-prac.yml
```

### ex2 包含兩個task，一個for Linux系統執行，另一個for Rocky
```
---    
-name: Play2
     hosts: node
     remote_user: dynasafe
     gather_facts: true
     
    tasks: 
     -name: Rocky execution 
      ansible.builtin.debug:
       msg: "{{ Rocky execution }}" 
       when: ansible_facts.distribution == "Rocky"
    
     -name: Linux execution 
      ansible.builtin.debug:
        msg: "{{ Linux execution }}" 
       when: ansible_facts.distribution == "Linux"
```
上傳

驗證
```
ansible-playbook when-prac.yml
```

### ex3 撰寫一個使用command模組的task，並且只有被控制節點的系統可以執行。藉由修改第一個task的判斷依據來控制第二個task是否執行或跳過。
```
---    
-name: Play3
     hosts: node
     remote_user: dynasafe
     gather_facts: true
     
    tasks: 
     -name: Rocky execution 
      ansible.builtin.command:
       echo " Rocky execution " 
       when: ansible_facts.distribution == "Rocky"
       register: result
       
     -name: Task2 
      ansible.builtin.debug:
        msg: "{{ Be executed }}" 
       when: result is succeeded
```
上傳

驗證
```
ansible-playbook when-prac.yml
```

### 任務區塊
#### Why
若符合判斷可以一次執行多個任務
```
tasks:
 -name: Block1
  block:
   -name: Echo1
    ansible.builtin.command: echo "Echo1"
   -name: Echo2
    ansible.builtin.command: echo "Echo2"
   when: ansible_facts['distribution'] == 'Linux'
```
### 錯誤處理
```
tasks:
 -name: Block1
  block:
   -name: Echo1
    ansible.builtin.command: /bin/false
  rescue:
   -ansible.builtin.debug:
    msg: "Fix this Issue"
```
### 事件處理
```
Task狀態改變時，才會觸發notify
tasks:
 -name: Trigger Notify
  ansible.builtin.command:
   echo "Notify Handler"
  notify:
   -Handler1

handlers:
 -name: Handler1
  ansible.builtin.debug:
   msg: "Be triggered"
```
### ex1 撰寫包含一個task，並且在task狀態改變後，觸發Handler
創建handler-prac.yml在Lesson3中
```
---
-name: Trigger Handler
 hosts: node
 remote_user: dynasafe
 gather_facts: false

tasks:
 -name: Trigger Handler
  ansible.builtin.command:
   echo "Trigger Handler"
  notify:
   -FirstHandler 
    
handlers:
 -name: FirstHandler
  ansible.builtin.debug:
   msg: "Be Triggeded"
```
    
### Tags
#### Where can I define Tags
- Play
- Task
- Block
- Role
##### Special Tags
- always : 不用指定也會執行，除非特別略過 (--skip tags always)
- never : 不會執行，除非特別指定 (--tags never)

#### Why
- 選擇性執行任務
- 批量執行任務
- 提高可讀性、可維護性 

#### How to use Tags
`ansible-playbook <PLAYBOOK>.yml <OPTION>`
##### OPTION
![](https://hackmd.io/_uploads/B1FU0wsq3.png)

### ex1 撰寫一個Play，符合以下項目
1. 須包含兩個Task
2. 藉由指定Tags的方式，只執行第二個Tasks
3. 運行結果需要同時印出如下訊息
    1. "Tags practice in Lesson4"
    2. Mapping 1 to 5

#### Step0
創建tags.yml在Lesson4

```
---
-name: Tags Practice
 hosts: node
 remote_user: root
 gather_facts: false
 
 vars:
  key1: [1, 2, 3, 4, 5]
 
 tasks:
  -name: Firsy tasks
  ansible.builtin.debug:
   msg: "This is First tasks"
  -name: Second tasks
   tags:  "0724"
   block:
    -name: Print msg
     ansible.builtin.debug:
      msg: "This  is second task"
    -name: Mapping 1 to 5
     ansible.builtin.debug:
      msg: "{{ item }}"
     loop: "{{ key1 }}"
```
上傳

驗證
ansible-playbook ./tags.yml (全部執行)

ansible-playbook ./tags.yml --tags 0724 (執行tags)
 
### Templates
#### Why
 1. 動態生成配置文件
 2. 可讀性、維護性
 3. 跨平台和可移植性
 4. 可重用性 (重複使用)
 
#### How to use Templates
1. Creat Template file
2. Use Template mpdule
```
tasks:
 -name: Copy template to remote
  ansible.builtin.template:
   src: sample-template.j2 (本地的配置文件)
   dest: /tmp/sample-template (遠端路徑位置)
   owner: root (檔案的owner)
   group: root (檔案的group)
   mode: '0644' (檔案的權限)
```
 
 ### How to import variable in Templates
 ### ex1 撰寫一個template，裡面須包含以下變數
 1. 主機群組變數
 2. 主機變數
 3. Play變數
 4. 外部變數清單
 5. Managed Node的node name
 
 #### Step0 
 創建template.yml在lesson4中
 ```
---
 -name: Test Template
  hosts: node
  remote_user: root
  gather_facts: true
 
 vars:
  play_var: Variable from play
 
 vars files:
  -./vars/main.yml
 
 tasks:
  -name: Test Template
   ansible.builtin.template:
    src: template.j2
    dest: /tmp/template
```
 #### Step1
 在templates folder中創建template.j2檔
```
 # Group_var
 {{ group_var }}
 
 # Host_var
 {{ host_var }}
 
 # Play_var
 {{ play_var }}
 
 # File_var
 {{ file_var }}
 
 # ansible_nodename (ansible all -m gather_facts | grep node)
 {{ ansible_nodename }} 
```
 
驗證
 `ansible-playbook template.yml`
 `ansible all -m command -a "cat /tmp/template"`
 
### Jinja2
 - Jinja2-If
  ![](https://hackmd.io/_uploads/BkYRYqic2.png)

### ex1 撰寫一個template，需要滿足以下條件:
  1. 判斷Play的變數若大於10，就在template顯示node name

 #### Step0
 創建template-if.yml在Lesson4中
 ```
---
 -name: Template If
  hosts: node
  remote_user: root
  gather_facts: true
  
  vars:
   key1: 11
 
  tasks:
   -name: Template If
    ansible.builtin.template:
     src: if.j2
     dest: /tmp/if
```
    
 #### Step1
 創建if.j2檔
 ```
{% if key1 > 10 %}
 {{ ansible_nodename }} (ansible all -m gather_facts | grep node)
 {% endif %}
```
 
 驗證
 `ansible-playbook ./template-if.yml`
`ansible all -m command -a "cat /tmp/if"`
 
 - Jinja-For
 ![](https://hackmd.io/_uploads/HJy4yoo5h.png)

 ### ex1 撰寫一個template，需要滿足以下條件
  1. Mapping Play的變數，並且只要顯示小於6的變數
 
 #### Step0 
 創建template-for.yml在Lesson4中
 ```
---
 -name: Test For
  hosts: node
 remote_user: root
 gather_facts: false
 
 vars:
 key1: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
 
 tasks:
  -name: Test For
   ansible.builtin.template:
   src: for.j2
   dest: /tmp/for
```
 
 #### Step1
 創建for.j2在templates中
 ```
{% for item in key1 %}
 {% if item (小於) 6 %}
 {{ item }}
 {% endif %}
 {% endfor %}
```
 
 驗證
 `ansible-playbook template-for.yml`
 `ansible all -m command -a "cat /tmp/for"`
 
### Sample Playbook
 - How to start Nginx Service
 ```flow
 st=>start: 0
 e=>end: 成功
 op1=>operation: 規劃安裝步驟
 op2=>operation: 撰寫腳本
 op3=>operation: 運行腳本
 cond=>condition: 錯誤

 st->op1->op2->op3->cond
 cond(yes)->op2
 cond(no)->e
 ```
![](https://hackmd.io/_uploads/Hk8zCjo52.png)

- Write Playbook
 1. Install epel-release
 ```
-name: Install epel-release
  ansible.builtin.yum:
   name: epel-release
```
 2. Install Nginx
```
-name: Install Nginx
 ansible.builtin.yum:
  name: nginx
```
3. Update Nginx config
 goal: 
   1. 將nginx worker process改為VM CPU的兩倍
   2. 將nginx服務起在9001port
 ![](https://hackmd.io/_uploads/S1eSe3jq3.png)

 ![](https://hackmd.io/_uploads/B1Yvlni52.png)

 4. Allow firewall port
 ![](https://hackmd.io/_uploads/BJzRe2scn.png)

 5. Start Nginx service
 ```
-name: Start Nginx service
  ansible.builtin.service:
   name: nginx
   state: started
```
 ### Role
 - 是一種Ansible的組織單位，可以用來封裝、共享Ansible的任務和配置
 - 可以重複使用的模塊
 #### Why
 - 節省時間成本，提高生產力
 - 藉由模組化特性，易於維護及擴展
 
 #### 自動創建基本的Role folder
 `ansible-galaxy init <Role Name>`
 
 ### ex1 依序完成以下
 1. 撰寫一個Play，裡面包含兩個Task
 2. 使用ansible-galaxy自動創建一個名為firstRole的Role
 3. 將play的兩個Tasks移到firstRole當中
 #### Step0
 創建role.yml
 ```
---
- name: role Practice
  hosts: node
  remote_user: osboxes
  gather_facts: false

  tasks:
   - name: first tasks
   ansible.builtin.debug:
    msg: " This is first task "
   - name: second tasks
   ansible.builtin.debug:
    msg: " This is second task "
```
 #### Step1
 創建roles資料夾by controller terminal
 `mkdir roles`
 進到裡面後輸入
 `ansible-galaxy init firstrole`
 
 #### Step2
 Remote to Local
 把剛剛創建的tasks內容移到firstrole的tasks中的yml檔
 
 #### Step3 
 在role.yml下方引入role
 ```
roles:
  -role: firstrole
```
 驗證
 `ansible-playbool role.yml`
 
 ### How to use Role -Import tasks
```
 ---
 - include_tasks: task1.yml
 - include_tasks: task2.yml
```
 ### ex2 將ex1的Role拆分為多個tasks:
 #### Step0
 在tasks中創兩個yml檔
 把本來放在main.yml的內容分別放入那兩個yml中
 #### Step1
 main.yml中輸入
 ```
 ---
 - include_tasks: task1.yml
 - include_tasks: task2.yml
```
 
 ### How to use Role -Import whole role
 ```
 ---
 - include_tasks: task1.yml
 - include_tasks: task2.yml
 - include_role:
    name: nginx
```
 
 ### Tags with Role in Play
 ```
roles:
  - role: httpd
   tags: [web, httpd]
  - role: nginx
    tags: [web, nginx]
```
 
 - 查看Play的tags
 `ansible-playbook <playbook> --list-tags`
 
 ### ex0 使用ansible-galaxy自動創建兩個Role(httpd, nginx)，並且須符合以下條件:
 1. 需要包含兩個Tasks
 2. 使用include_tasks將Tasks引入到Role的main.yml
 3. 同樣引入Play，藉由定義Tags來選擇只執行nginx
 4. 在nginx role的task當中增加Tag，並且列出所有nginx的tags
 
 #### Step0
 在roles中自動創建
 `ansible-galaxy init httpd`
 `ansible-galaxy init nginx`
 
 include進main
 
 #### Step1
 ```
- role: nginx
   tags: [nginx, web]
- role: httpd
   tags: [httpd, web]
```
 
 #### Step2
 在nginx role的firsrtask中加tag
 `tags: ['newTag']`
 #### Step3
 把本來main.yml中的include_tasks改成import_tasks
 
 驗證
 `ansible-playbook role.yml --tags nginx`
 
 驗證
 `ansible-playbook ./role.yml --tags nginx --list-tasks`

 ### Variable
 ![](https://hackmd.io/_uploads/HkaEaNC9n.png)

 ### ex0 創建一個新的Role，並符合以下條件:
 1. 此Role需要使用Debug Module顯示變數
 2. 分別在Play、vars in Role定義相同Key的變數，並驗證其優先級
 #### Step0
 在roles中創一個debug folder
 裡面放tasks folder、vars folder
 在vars folder裡面創main.yml
 `key1: "The value from file"`
 在tasks folder裡面創main.yml
 ```
---
 - name: Print Var
   debug:
    var: key1
```
 #### Step1
 在role.yml中
 `- role: debug`
 
 #### Step2 
 在role.yml中
 ```
vars:
  key1: "Value from Play"
```
 -> Role中定義的變數 > Play定義的變數
 
 ### 引用相同Role
 ### ex1 在一個Play同時引入兩個相同Role，並練習以下操作
 1. 使用引入變數不同，讓Role執行兩次 (X)
 2. 藉由修改meta的方式，讓Role執行兩次
#### Step0
 在debug folder中創立meta folder
 裡面創建main.yml
` allow_duplicates: true`
 
## 實際運用
 ### SOSReport
 [Code on Github](https://github.com/eugene1031/CNS-Intern/tree/bd841e13d80dfef372aef26a896d2e832bca0643/SOSReport)
 
 # Kubernetes
   