# 
HeadHunterSchool homework: 1. Git, task #3
---------

```
git init
```

##### 1) Коммит содержищий в себе 1 файл: task3.txt содержащий любой 4х строчний текст - коммит меседж "commit <%username> 2" где <%username> -  ваш ник на github'е
```
printf "%s\n%s\n%s\n%s\n" "line1" "line2" "line3" "line4" > task3.txt
git hash-object -w task3.txt
```
> 84275f9939456e87efd6932bdf7fe01d52a53116

```
git update-index --add --cacheinfo 100644 \
84275f9939456e87efd6932bdf7fe01d52a53116 task3.txt
```

```
git write-tree
```
> eed99f812c728686a6757ab5a7d9f0c80e2f56cc


```
echo 'commit Iskuskov 1' | git commit-tree eed99f
```
> 2b0c67b9507a1c614f5a3e9029f38c3f8a68d4b0



##### 2) Коммит содержащий в себе 2 файла: task3_new.txt - содержащий 2 строчки любого текста и task3.txt содержащий любой 4х строчний текст (другой нежели в п.1) - коммит меседж "commit <%username> 2"
```
printf "%s\n%s\n%s\n%s" "update_line1" "update_line2" "update_line3" "update_line4" > task3.txt
printf "%s\n%s" "new_line1" "new_line2" > task3_new.txt
```

```
git update-index task3.txt
git update-index --add task3_new.txt
git write-tree
```
> 2fc96a6ab7c1d81de6f754fcc51a02f6b52ca434

```
echo 'commit Iskuskov 2' | git commit-tree 2fc96a -p 2b0c67
```
> 108ca162f5385c6ffeb11c020aaeeb5bdae2b3fd


##### 3) Коммит содержищий в себе новую дирректорию gittask с файлом task3.txt первой версии - коммит меседж "commit <%username> 3"

```
git read-tree --prefix=gittask eed99f
git write-tree
```
> b41de6ec2ee9cf348047b31fe18ea71202eec9e1

```
echo 'commit Iskuskov 3' | git commit-tree b41de6 -p 108ca1
```
> cf6148f4b31b70a9cb69e9381004bc2d2b43e252

```
git update-ref refs/heads/master cf6148
```


##### Push repo
```
git remote add origin https://github.com/Iskuskov/hh_git_3.git
git push origin --all
```




