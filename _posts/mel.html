# SQBW制作命令集

本文档介绍了SQBW制作命令集的使用方法和相关说明。

## 目录
1. [简介](#简介)
2. [命令格式](#命令格式)
3. [常用命令](#常用命令)
4. [注意事项](#注意事项)
5. [参考资料](#参考资料)

## 简介
SQBW制作命令集是用于简化和加速开发流程的工具集，旨在提高效率并减少人为错误。

## 命令格式
所有命令均遵循以下格式：
```
sqbw <command> [options]
```
- `<command>`: 指定要执行的操作。
- `[options]`: 可选参数，用于调整命令行为。

## 常用命令
### 初始化项目
```
sqbw init
```
初始化一个新的项目。

### 构建项目
```
sqbw build
```
构建当前项目。

### 部署项目
```
sqbw deploy
```
将项目部署到目标环境。

## 注意事项
- 确保安装了最新版本的SQBW工具。
- 在执行命令前，请备份重要数据。

## 参考资料
- [SQBW官方文档](#)
- [常见问题解答](#)
## 示例代码

以下是命令集的代码：

```bash
// ========== 主窗口创建过程（更新版） ========== //
global proc showCustomWindow() {
    if (`window -exists customWin`) deleteUI customWin;

    window -title "渲染工具" -widthHeight 400 300 customWin;
    gridLayout -numberOfColumns 3 -cellWidth 130 -cellHeight 75;

    string $btn;
    int $i;
    for ($i = 0; $i < 12; $i++) {
        $btn = "btn_"+$i;
        
        // 第一行第一列（索引0）
        if ($i == 0) {
            button -label "另存渲染文件" -command "saveRenderFileProc" $btn;
        } 
        // 第一行第二列（索引1）添加新功能
        else if ($i == 1) {
            button -label "剔除未引用节点" 
                   -command "cleanUnloadedReferences" 
                   -annotation "清理所有未加载的引用节点" 
                   $btn;
        }
        // 第一行第三列（索引2）添加新功能
        else if ($i == 2) {
            button -label "导入HH天球材质" 
                   -command "importLayerFile" 
                   -annotation "导入黄昏天球材质" 
                   $btn;
        }
        // 第二行第一列（索引3）添加新功能
        else if ($i == 3) {
            button -label "导入CH灯光" 
                   -command "importLayerFile1" 
                   -annotation "导入CH灯光" 
                   $btn;
        }
        // 第四行第三列（索引11）添加新功能
        else if ($i == 11) {
            button -label "导入文件" 
                   -command "importLayerFile0" 
                   -annotation "导入任意文件" 
                   $btn;
        }
        else {
            button -label "开发中" -enable false $btn;
        }
    }
    showWindow customWin;
}


// ========== 清理未引用节点功能 ========== //
global proc cleanUnloadedReferences() {
    // 获取所有引用节点（排除默认节点）
    string $allRefs[] = `ls -type "reference"`;
    string $excludeList[] = {"sharedReferenceNode", "sharedReferenceNode1"};

    // 进度窗口初始化
    int $total = size($allRefs);
    progressWindow -title "清理引用文件" 
                  -status "正在扫描..." 
                  -maxValue $total 
                  -isInterruptable true;

    int $cleanedCount = 0;
    int $progress = 0;

    for ($ref in $allRefs) {
        // 检查中断请求
        if (`progressWindow -query -isCancelled`) break;

        // 排除系统节点
        if (!stringArrayContains($ref, $excludeList)) {
            int $isLoaded = `referenceQuery -isLoaded $ref`;
            string $refPath = `referenceQuery -filename $ref`;

            // 更新进度信息
            progressWindow -edit 
                          -status ("正在处理：" + $ref) 
                          -progress $progress;

            // 清理未加载的引用
            if (!$isLoaded) {
                int $status = catch(`file -removeReference -referenceNode $ref`);
                if ($status == 0) {
                    print("成功移除引用：" + $ref + "\n路径：" + $refPath + "\n");
                    $cleanedCount++;
                }
            }
        }
        $progress++;
    }

    progressWindow -endProgress;
    confirmDialog -title "操作完成" 
                 -message ("已清理 " + $cleanedCount + "/" + $total + " 个未加载引用") 
                 -button "确定";
}
// ========== 核心保存功能（完全修正版） ========== //
global proc saveRenderFileProc() {
    // 声明所有变量
    string $currentFile, $pattern, $newFile;
    string $parts[], $newParts[];
    int $i, $count, $hasReplaced, $ver;

    // 正确获取文件路径（带查询标志）
    $currentFile = `file -q -sceneName`;
    if ($currentFile == "") {
        confirmDialog -t "警告" -m "请先保存场景" -b "确定";
        return;
    }

    // === 文件名处理 === //
    $pattern = "^(.+)\\.(ep\\d+seq\\d+sc\\d+)\\.lay_layout\\.(v\\d+)\\.(ma|mb)$";
    
    // 修正1：正确的match调用方式
    int $numMatches = `match $pattern $currentFile`;

    if ($numMatches > 0) {
        // 提取匹配组
        string $prefix = `matchGroup 1`;
        string $epInfo = `matchGroup 2`;
        string $version = `matchGroup 3`;
        string $ext = `matchGroup 4`;
        $newFile = $prefix + "." + $epInfo + ".lgt_final." + $version + "." + $ext;
    } else {
        // 备用处理方案
        $parts = {};
        $count = `tokenize $currentFile "." $parts`;
        $hasReplaced = 0;

        for ($i = 0; $i < $count; $i++) {
            if ($parts[$i] == "lay_layout") {
                $parts[$i] = "lgt_final";
                $hasReplaced = 1;
                break;
            }
        }

        if (!$hasReplaced && $count >= 3) {
            $newParts = {};
            for ($i = 0; $i < ($count - 2); $i++) {
                $newParts[size($newParts)] = $parts[$i];
            }
            $newParts[size($newParts)] = "lgt_final";
            $newParts[size($newParts)] = $parts[$count - 2];
            $newParts[size($newParts)] = $parts[$count - 1];
            $parts = $newParts;
        }
        $newFile = `stringArrayToString $parts "."`;
    }

    // === 版本控制（修正2：使用filetest命令） === //
    $ver = 1;
    string $baseName = `substitute "v\\d+" "" $newFile`;
    string $currentExt = `substitute ".*(\\..+)$" "\\1" $newFile`;
    
    while (`filetest -f $newFile`) {
        $newFile = `substitute "v\\d+" ("v" + $ver) $baseName` + $currentExt;
        $ver++;
    }

    // 执行保存
    file -rename $newFile;
    file -save -force -type "mayaAscii";

    confirmDialog -t "保存成功" -m ("新路径：\n" + $newFile) -b "确定";
}


// ========== 导入HH天球材质增强方案（带错误处理） ========== //
global proc importLayerFile() {
    string $filePath = "D:/Y/SQBW/ENV/HH/F_Layer.mb"; // 注意路径使用正斜杠
    
    // 验证文件是否存在
    if (!`file -query -exists $filePath`) {
        warning("文件不存在: " + $filePath);
        return;
    }
    
    // 执行导入操作（带命名空间处理）
    file -import 
        -type "mayaBinary" 
        -namespace "" // 这里可以自定义空间域名
        -options "v=0" 
        $filePath;
    
    print("成功导入资产: " + $filePath + "\n");
}

// ========== 导入CH灯光增强方案（带错误处理） ========== //
global proc importLayerFile1() {
    string $filePath = "D:/Y/SQBW/ENV/light/CHA_LIG.mb"; // 注意路径使用正斜杠
    
    // 验证文件是否存在
    if (!`file -query -exists $filePath`) {
        warning("文件不存在: " + $filePath);
        return;
    }
    
    // 执行导入操作（带命名空间处理）
    file -import 
        -type "mayaBinary" 
        -namespace "" // 这里可以自定义空间域名
        -options "v=0" 
        $filePath;
    
    print("成功导入资产: " + $filePath + "\n");
}
// ========== 导入文件 ========== //
global proc importLayerFile0() {
    string $filePath = `fileDialog`;
    if ($filePath == "") return;
    // 验证文件是否存在
    if (!`file -query -exists $filePath`) {
        warning("文件不存在: " + $filePath);
        return;
    }
    
    // 执行导入操作（带命名空间处理）
    file -import 
        -type "mayaBinary" 
        -namespace "" // 这里可以自定义空间域名
        -options "v=0" 
        $filePath;
    
    print("成功导入资产: " + $filePath + "\n");
}
// ========== 执行入口 ========== //
showCustomWindow;

```

通过以上命令，可以快速完成项目的初始化、构建和部署。