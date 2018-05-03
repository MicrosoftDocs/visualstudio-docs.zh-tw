---
title: 管理外部工具
ms.date: 11/20/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.externaltools
helpviewer_keywords:
- external tools [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eeeee2e6e7ae5d043124faaa79bc6bad7c527702
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="manage-external-tools"></a>管理外部工具

您可以使用 [工具]，從 Visual Studio 內部呼叫外部工具。 [工具] 功能表中有提供一些預設的工具，且您可以另外自行加入可執行檔來自訂該功能表。

## <a name="tools-available-on-the-tools-menu"></a>[工具] 功能表上提供的工具

[工具] 功能表包含數個內建命令，例如：

* [延伸模組和更新] 可用來[管理 Visual Studio 延伸模組](finding-and-using-visual-studio-extensions.md)
* [程式碼片段管理員] 可用來[組織程式碼片段](code-snippets.md)
* [PreEmptive Protection - Dotfuscator] 可用來啟動 [Dotfuscator Community Edition (CE)](dotfuscator/index.md) (若[已安裝](dotfuscator/install.md)的話)
* [自訂] 可用來[自訂功能表和工具列](how-to-customize-menus-and-toolbars-in-visual-studio.md)
* [選項] 可用來[設定各種不同的 Visual Studio IDE 和其他工具選項](reference/options-dialog-box-visual-studio.md)

## <a name="add-new-tools-to-the-tools-menu"></a>將新的工具新增至 [工具] 功能表

您可加入外部工具，讓它顯示在 [工具] 功能表。

1. 選擇 [工具] > [外部工具]，以開啟 [外部工具] 對話方塊。

1. 按一下 [加入]，然後填入資訊。 例如，下列輸入內容會讓 **Windows 檔案總管**的開啟位置，會是於 Visual Studio 中目前所開啟之檔案所在的目錄：

   * 標題：`Open File Location`

   * 命令：`explorer.exe`

   * 引數：`/root, "$(ItemDir)"`

   ![[外部工具] 對話方塊](media/external-tools-dialog.png)

以下是在定義外部工具時可以使用的引數完整清單：

|名稱|引數|描述|
|----------|--------------|-----------------|
|項目路徑|$(ItemPath)|目前檔案的完整檔案名稱 (磁碟機 + 路徑 + 檔案名稱)。|
|項目目錄|$(ItemDir)|目前檔案的目錄 (磁碟機 + 路徑)。|
|項目檔名|$(ItemFilename)|目前檔案的檔案名稱 (檔案名稱)。|
|項目副檔名|$(ItemExt)|目前檔案的副檔名。|
|目前的行|$(CurLine)|程式碼視窗中滑鼠游標目前的行位置。|
|目前的資料行|$(CurCol)|程式碼視窗中滑鼠游標目前的資料行位置。|
|目前的文字|$(CurText)|選取的文字。|
|目標路徑|$(TargetPath)|要建置之項目的完整檔案名稱 (磁碟機 + 路徑 + 檔案名稱)。|
|目標目錄|$(TargetDir)|要建置之項目的目錄。|
|目標名稱|$(TargetName)|要建置之項目的檔案名稱。|
|目標副檔名|$(TargetExt)|要建置之項目的副檔名。|
|二進位檔目錄|$(BinDir)|正在建置之二進位檔的最終位置 (定義為磁碟機 + 路徑)。|
|專案目錄|$(ProjDir)|目前專案的目錄 (磁碟機 + 路徑)。|
|專案檔名|$(ProjFileName)|目前專案的檔案名稱 (磁碟機 + 路徑 + 檔案名稱)。|
|方案目錄|$(SolutionDir)|目前方案的目錄 (磁碟機 + 路徑)。|
|方案檔名|$(SolutionFileName)|目前方案的檔案名稱 (磁碟機 + 路徑 + 檔案名稱)。|

> [!NOTE]
> IDE 狀態列會顯示 **目前這一行**和**目前資料行**的變數，以指出插入點在作用中**程式碼編輯器**的位置。 **目前的文字**變數則會傳回在該位置選取的文字或程式碼。

## <a name="see-also"></a>另請參閱

- [C/C++ 建置工具](/cpp/build/reference/c-cpp-build-tools)
