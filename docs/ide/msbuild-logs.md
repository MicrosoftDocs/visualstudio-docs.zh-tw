---
title: 疑難排解及建立 MSBuild 問題的記錄檔
description: 瞭解如何診斷 Visual Studio 專案中的組建問題，並視需要建立要傳送給 Microsoft 的記錄以進行調查。
ms.custom: SEO-VS-2020
ms.date: 06/27/2019
ms.technology: vs-ide-compile
ms.topic: troubleshooting
helpviewer_keywords:
- msbuild logs"
author: corob-msft
ms.author: corob
manager: jmartens
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Generate build logs for msbuild projects to collect helpful information when troubleshooting issues.
ms.openlocfilehash: d9308bff68a5a5377c025bba5861ac344dcb0326
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880485"
---
# <a name="troubleshoot-and-create-logs-for-msbuild-problems"></a>疑難排解及建立 MSBuild 問題的記錄檔

下列程序可協助您診斷 Visual Studio 專案中的建置問題，並在有需要時建立記錄檔，以便傳送給 Microsoft 調查。

## <a name="a-property-value-is-ignored"></a>忽略屬性值

如果專案屬性似已設為特定值，但對組建沒有作用，請遵循下列步驟：

1. 開啟與您 Visual Studio 版本對應的 Visual Studio 開發人員命令提示字元。
1. 替換解決方案路徑、組態和專案名稱之後，執行下列命令：

    ```cmd
    msbuild /p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /pp:out.xml MyProject.vcxproj
    ```

    此命令會產生「處理過的」msbuild 專案檔 (out.xml)。 您可以搜尋該檔案的特定屬性，查看定義的位置。

組建會取用屬性的最後定義。 如果屬性設定了兩次，第二個值會覆寫第一個值。 此外，MSBuild 會分數個階段評估專案：

- PropertyGroups 和 Imports
- ItemDefinitionGroups
- ItemGroups
- 目標

因此，假設順序如下：

```xml
<PropertyGroup>
   <MyProperty>A</MyProperty>
</PropertyGroup>
<ItemGroup>
   <MyItems Include="MyFile.txt"/>
</ItemGroup>
<ItemDefinitionGroup>
  <MyItems>
      <MyMetadata>$(MyProperty)</MyMetadata>
  </MyItems>
</ItemDefinitionGroup>
<PropertyGroup>
   <MyProperty>B</MyProperty>
</PropertyGroup>
```

"MyFile.txt" 項目的 "MyMetadata" 值在建置期間評估為 "B" (不是 "A" 也不是空白)

## <a name="incremental-build-is-building-more-than-it-should"></a>建置超過應有的累加組建

如果 MSBuild 非必要地重建專案或專案項目，請建立詳細或二進位的組建記錄檔。 您可以在記錄檔中搜尋非必要建置或編譯的檔案。 輸出看起來會像這樣：

```output
  Task "CL"

  Using cached input dependency table built from:

  F:\test\Project1\Project1\Debug\Project1.tlog\CL.read.1.tlog

  Outputs for F:\TEST\PROJECT1\PROJECT1\PROJECT1.CPP:
  F:\TEST\PROJECT1\PROJECT1\DEBUG\PROJECT1.OBJ
  Project1.cpp will be compiled because F:\TEST\PROJECT1\PROJECT1\PROJECT1.H was modified at 6/5/2019 12:37:09 PM.

  Outputs for F:\TEST\PROJECT1\PROJECT1\PROJECT1.CPP:
  F:\TEST\PROJECT1\PROJECT1\DEBUG\PROJECT1.OBJ

  Write Tracking Logs:
  Debug\Project1.tlog\CL.write.1.tlog
```

如果您要在 Visual Studio IDE 中建置 (搭配詳盡的輸出視窗詳細資訊)，則 [輸出視窗] 會顯示每個專案為何不是最新的原因：

```output
1>------ Up-To-Date check: Project: Project1, Configuration: Debug Win32 ------

1>Project is not up-to-date: build input 'f:\test\project1\project1\project1.h' was modified after the last build finished.
```

## <a name="create-a-binary-msbuild-log"></a>建立二進位 msbuild 記錄檔

1. 開啟適用於您 Visual Studio 版本的開發人員命令提示字元
1. 在命令提示字元中，執行下列任一命令。 (請記得使用實際的專案和組態值。)：

    ```cmd
    Msbuild /p:Configuration="MyConfiguration";Platform="x86" /bl MySolution.sln
    ```

    或

    ```cmd
    Msbuild /p:/p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /bl MyProject.vcxproj
    ```

Msbuild.binlog 檔案會建立在您執行 MSBuild 的目錄中。 您可以使用 [Msbuild Structured Log Viewer](http://www.msbuildlog.com/) (Msbuild 結構化記錄檢視器) 檢視與搜尋。

## <a name="create-a-detailed-log"></a>建立詳細的記錄檔

1. 從 Visual Studio 主功能表中，移至 [**工具**  >  **選項**  >  **專案和方案**  > **組建及執行**]。
1. 兩個下拉式方塊中的 [Msbuild project build verbosity] \(MSBuild 專案組建詳細資料\) 都設為 [詳細]。 第一個控制項是 **輸出視窗** 中的組建詳細資訊，第二個則 \<projectname\> 是在組建期間，在每個專案的中繼目錄中所建立的 .log 檔案中控制組建詳細資訊。
2. 在 Visual Studio 開發人員命令提示字元中，輸入下列任一命令，替換實際的路徑和組態值：

    ```cmd
    Msbuild /p:Configuration="MyConfiguration";Platform="x86" /fl MySolution.sln
    ```

    或

    ```cmd
    Msbuild /p:/p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /fl MyProject.vcxproj
    ```

    Msbuild.log 檔案會建立在您執行 msbuild 的目錄中。

## <a name="see-also"></a>另請參閱

- [Visual Studio 疑難排解](/troubleshoot/visualstudio/welcome-visual-studio/)
