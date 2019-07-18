---
title: VSCT 編譯器命令列旗標 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b0e70d6695b76df9a6ef66586713e27a61697ae
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66332899"
---
# <a name="vsct-compiler-command-line-flags"></a>VSCT 編譯器命令列旗標
Visual Studio 命令資料表 (VSCT) 編譯器會提供命令列參數，以確保成功編譯.vsct 檔案。

## <a name="command-line-parameters"></a>命令列參數
 若要檢視從基本 VSCT 說明[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]**命令** 視窗中，瀏覽至*Visual Studio SDK 安裝路徑*\VisualStudioIntegration\Tools\Bin\ 資料夾並輸入：

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
> 字元-(dash) 及 / （斜線） 是這兩個可接受的標記法來表示命令列參數。

 可接受的旗標，這些代表什麼意思如下所示。

|參數|描述|
|------------|-----------------|
|-D|指定任何其他已定義的符號。|
|-I|表示額外的 include 路徑，應在解析檔案參考時使用。|
|-L|指定<xref:System.Globalization.CultureInfo>文化特性名稱，例如"EN-US"。|
|-E|發出C#後面接著命令項目，指定的命名空間中的物件 [C&#124;H&#124;N]:*filename*，C = C#，H =C++標頭，N = 命名空間。 需要適用於 C# 命名空間。|
|-v|詳細資訊輸出。|

 -L 選項會指示編譯器選取一組的字串，以產生對應到二進位檔.cto 檔指定<xref:System.Globalization.CultureInfo>文化特性名稱。 指定的文化特性名稱應該符合 [語言] 屬性的一或多個[Strings 元素](../../extensibility/strings-element.md).vsct 檔案中。 如果字串項目不有任何語言屬性時，它繼承自包含[CommandTable 元素](../../extensibility/commandtable-element.md)。

 .Vsct 檔可能有多個字串元素，而每個可能不同的語言屬性。 全球化之後，即可多次執行 VSCT 編譯器，然後變更 -L 選項，針對每個文化特性名稱。

 如果-L 參數所指定的文化特性名稱不符合任何字串項目的 Language 屬性，編譯器會嘗試比對語言和不在區域中。 例如，如果找不到"EN-US"，編譯器會嘗試使用"en"改為。 如果無法做到，就會嘗試目前的文化特性的作業系統。 如果無法做到，它將會編譯它找到的第一個字串元素。

 -E 參數可用來發出 c-style 標頭檔包含 [命令] 資料表中，所使用的符號，或發出 C# 檔案，其中包含命令符號的物件。

 -D 和-我交換器已有同名的 Cl.exe C 前置處理器旗標的語法。 -D 具有 X = Y 格式定義用於 XML 為基礎的擴充\<定義 > 測試`Condition`屬性。 -I include 路徑用來解析\<Include >， \<Extern > 和\<點陣圖 > 檔案參考。 如需詳細資訊，請參閱 < [VSCT XML Schema Reference](../../extensibility/vsct-xml-schema-reference.md)。

 VSCT 編譯器也可以反編譯先前建置的二進位檔案。 若要這樣做，請提供 二進位檔\<infile >。   如果 VSCT 編譯器所產生的二進位檔案，它將具有其已內嵌的符號，並會產生輸出中的符號名稱\<符號 > 輸出區段。 如果 CTC 編譯器所產生的二進位檔，則輸出會包含實際 Guid 和 Id。 產生的最新版本的 Ctc.exe *.ctsym 檔案是否為二進位的輸入檔的相同資料夾中，將從該檔案載入符號，並用於輸出。

## <a name="see-also"></a>另請參閱
- [Visual Studio 命令表檔案 (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT XML 結構描述參考](../../extensibility/vsct-xml-schema-reference.md)
- [VSPackage 如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)