---
title: .VSCT 編譯器命令列旗標 |Microsoft Docs
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
ms.openlocfilehash: 71634a007019dd39e843ccc63af1c3188f778ea9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722022"
---
# <a name="vsct-compiler-command-line-flags"></a>VSCT 編譯器命令列旗標
Visual Studio 命令資料表（.VSCT）編譯器會提供命令列參數，以確保 .vsct 檔案的編譯成功。

## <a name="command-line-parameters"></a>命令列參數
 若要從 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]**命令**視窗中查看基本 .vsct 說明，請流覽至*Visual Studio SDK 安裝路徑*\VisualStudioIntegration\Tools\Bin\ 資料夾，並輸入：

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
> 字元-（破折號）和/（斜線）都是可接受的標記法來表示命令列參數。

 可接受的旗標及其意義如下所示。

|參數|描述|
|------------|-----------------|
|-D|指定任何其他已定義的符號。|
|-I|指出解析檔案參考時應該使用的其他 include 路徑。|
|-L|指定 <xref:System.Globalization.CultureInfo> 文化特性名稱，例如 "en-us"。|
|-E|在C#指定的命名空間中，為命令專案發出物件，後面&#124;接著&#124;[c HN]： filename C#，其中 C C++ =，H = header，N = namespace。 需要命名空間C#。|
|-v|詳細資訊輸出。|

 -L 參數會指示編譯器選取一組字串，以產生對應至指定 <xref:System.Globalization.CultureInfo> 文化特性名稱的 cto 檔案。 指定的文化特性名稱應符合 .vsct 檔案中一個或多個[String 元素](../../extensibility/strings-element.md)的 Language 屬性。 如果 String 元素沒有 Language 屬性，它會繼承自包含的[CommandTable 元素](../../extensibility/commandtable-element.md)。

 .Vsct 檔案可能會有多個字串元素，而且每個都有不同的 Language 屬性。 全球化是藉由執行 .VSCT 編譯器多次，並變更每個文化特性名稱的-L 參數來達成。

 如果-L 參數所提供的文化特性名稱與任何字串專案的 Language 屬性不相符，編譯器會嘗試比對語言，而不是區域。 例如，如果找不到 "en-us"，編譯器會改為嘗試 "en"。 失敗了，它會嘗試作業系統目前的文化特性。 失敗了，它會編譯它找到的第一個字串元素。

 -E 參數可以用來發出 C 樣式的標頭檔，其中包含命令資料表所使用的符號，或發出C#包含命令符號之物件的檔案。

 -D 和-I 參數具有具有相同名稱之 Cl C 預處理器旗標的語法。 具有 X = Y 格式的-D 定義會用於擴充 `Condition` 屬性中的 XML 型 \<Defined > 測試。 -I 包含路徑可用來解析 \<Include >、\<Extern > 和 \<Bitmap 檔案參考。 如需詳細資訊，請參閱[.VSCT XML 架構參考](../../extensibility/vsct-xml-schema-reference.md)。

 .VSCT 編譯器也可以反編譯先前建立的二進位檔案。 若要這麼做，請提供 \<infile > 的二進位檔案。   如果二進位檔案是由 .VSCT 編譯器所產生，它的符號就已經內嵌，而且會在輸出的 \<Symbols > 區段中產生符號名稱的輸出。 如果二進位檔是由 .CTC 編譯器所產生，輸出將會包含實際的 Guid 和識別碼。 如果目前的 .Ctc 版本所產生的 *. .ctsym 檔案與二進位輸入檔位於相同的資料夾，則會從該檔案載入符號，並用於輸出。

## <a name="see-also"></a>請參閱
- [Visual Studio 命令表檔案 (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT XML 結構描述參考](../../extensibility/vsct-xml-schema-reference.md)
- [VSPackage 如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)