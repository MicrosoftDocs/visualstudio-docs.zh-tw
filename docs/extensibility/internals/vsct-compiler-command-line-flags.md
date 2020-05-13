---
title: VSCT 編譯器命令行標誌 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e4ee29710049453c3163c366eccf96e257b6028d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703961"
---
# <a name="vsct-compiler-command-line-flags"></a>VSCT 編譯器命令列旗標
可視化工作室命令表 (VSCT) 編譯器提供命令列交換機,以確保成功編譯 .vsct 檔。

## <a name="command-line-parameters"></a>命令列參數
 要檢視從[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]**指令**視窗的基本 VSCT 說明,請檢視*Visual Studio SDK 安裝路徑*[VisualStudio 整合式]工具\Bin] 資料夾與類型:

```
vsct /?
```

 這會傳回：

```
Microsoft (R) Visual Studio (R) Command Table Compiler Version 3.00.2000

Syntax: vsct <infile> [<outfile>] [-S[symbols file]] [-D<preprocessor-define>]*
[-I<include-path>]* [-L<language>] [-E[C|H|N]:<name>]

  -D    Specify any additional preprocessor defines
  -I    Indicate what additional include paths to send to the preprocessor
  -L    Specify the language to use when selecting strings
  -E    Emit C# objects in the specified namespace for command items,
        followed by [L|F|H|N]:<value>
        F = Name of the file to emit (used if -EL is provided)
        L = Name of a language providing a CodeDOM provider
        N = namespace (required if -EL is provided)
        H = C++ header
  -c    Clean build skipping dependency checks
  -v    Verbose output
```

> [!NOTE]
> 字元 - (短劃線) 和 / (前斜杠) 都是用於指示命令列參數的公認符號。

 可接受的標誌及其含義如下所示。

|Switch|描述|
|------------|-----------------|
|-d|指定任何其他定義的符號。|
|-I|指示解析檔引用時應使用的其他包含路徑。|
|-l|指定<xref:System.Globalization.CultureInfo>區域性名稱,例如"en-US"。|
|-E|在指定命名空間中為命令項發出 C# 物件,後跟 [C&#124;H&#124;N]:*檔案名*C = C#,H = C++標頭,N = 命名空間。 C# 需要命名空間。|
|-v|詳細輸出。|

 -L 開關指示編譯器選擇一組字串來生成對應於給定<xref:System.Globalization.CultureInfo>區域性名稱的二進位 .cto 檔。 指定的區域性名稱應與 .vsct 檔中一個或多個[字串元素](../../extensibility/strings-element.md)的語言屬性匹配。 如果 Strings 元素沒有語言屬性,則從包含[命令表元素](../../extensibility/commandtable-element.md)繼承它。

 .vsct 檔案可能有多個字串元素,並且每個元素可能具有不同的語言屬性。 全球化是通過多次運行 VSCT 編譯器並更改每個區域性名稱的 -L 開關來實現的。

 如果 -L 開關提供的區域性名稱與任何 Strings 元素的語言屬性不匹配,編譯器將嘗試匹配該語言,而不是區域。 例如,如果找不到"en-US",編譯器將嘗試"en"。" 否則,它將嘗試操作系統的當前區域性。 否則,它將編譯它找到的第一個字串元素。

 -E 開關可用於發出包含命令表使用的符號的 C 樣式標頭檔,或發出包含命令符號物件的 C# 檔。

 -D 和 -I 開關具有具有相同名稱的 Cl.exe C 預處理器標誌的語法。 -具有 X_Y 格式的 D 定義\<`Condition`用於擴充屬性中 基於 XML 的已定義>測試。 -我包括用於解析\<包含>、extern \<\<> 和 位圖>檔引用的路徑。 有關詳細資訊,請參閱[VSCT XML 架構參考](../../extensibility/vsct-xml-schema-reference.md)。

 VSCT 編譯器還可以取消編譯以前構建的二進位檔案。 為此,為\<infile>提供二进制文件。   如果二進位檔由 VSCT 編譯器生成,它將已嵌入其符號,並將在\<輸出的符號>部分中生成具有符號名稱的輸出。 如果二進位檔由 CTC 編譯器生成,則輸出將包含實際的 GUID 和 DO。 如果當前版本的 Ctc.exe 生成的 _.ctsym 檔與二進位輸入檔位於同一資料夾中,則符號將從該檔載入並用於輸出。

## <a name="see-also"></a>另請參閱
- [Visual Studio 命令表檔案 (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT XML 結構描述參考](../../extensibility/vsct-xml-schema-reference.md)
- [VSPackage 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
