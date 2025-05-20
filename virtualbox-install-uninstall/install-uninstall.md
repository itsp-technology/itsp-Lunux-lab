## 1. Serach the virtualbox in the RHEL VM 

```bash
sudo yum search virtualbox
```
```bash
output
================================== Name & Summary Matched: virtualbox ===================================
VirtualBox-6.1.x86_64 : Oracle VM VirtualBox
VirtualBox-7.0.x86_64 : Oracle VM VirtualBox
VirtualBox-7.1.x86_64 : Oracle VirtualBox

```

## 1. select and install virtual box 
```bash
sudo yum install  VirtualBox-6.1.x86_64
```


## 1. grep the virtual box installed version 
```bash
sudo yum list installed | grep VirtualBox 
```
**Output**:
  ```
  VirtualBox-6.1.x86_64                            6.1.50_161033_el9-1                 @virtualbox         
  ```

## 1. 
```bash
sudo yum remove  VirtualBox-*   virtualbox-*

```

