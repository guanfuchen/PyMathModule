# Gradle

---
## 相关语法

### 条件语法

```
if (Os.isFamily(Os.FAMILY_WINDOWS)) {
        println "WINDOWS"
} else {
        println "NOT WINDOWS"
}
```

---
## 检测系统环境

针对当前系统是WINDOWS、MAC还是UNIX。

```
import org.apache.tools.ant.taskdefs.condition.Os
task checkWin() << {
    if (Os.isFamily(Os.FAMILY_WINDOWS)) {
        println "WINDOWS"
    }
    if (Os.isFamily(Os.FAMILY_MAC)) {
        println "FAMILY_MAC"
    }
    if (Os.isFamily(Os.FAMILY_UNIX)) {
        println "FAMILY_UNIX"
    }
}
```

---
## 参考资料

- [If else condition in Gradle](https://discuss.gradle.org/t/if-else-condition-in-gradle/20395)
- [How to detect the current OS from gradle](https://stackoverflow.com/questions/11235614/how-to-detect-the-current-os-from-gradle)
