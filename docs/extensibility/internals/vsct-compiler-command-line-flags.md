---
title: .VSCT 編譯器 Command-Line 旗標 |Microsoft Docs
description: Visual Studio 命令資料表編譯器會提供命令列選項，以確保 .vsct 檔案的編譯成功。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 8d60b248a4941d176ac6ba4e808a94dbc67efbe7
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97488007"
---
# <a name="vsct-compiler-command-line-flags"></a>VSCT 編譯器命令列旗標
Visual Studio 命令表格 (.VSCT) 編譯器提供命令列參數，以確保 .vsct 檔的編譯成功。

## <a name="command-line-parameters"></a>命令列參數
 若要從命令視窗中查看基本的 .VSCT 說明 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]  ，請流覽至 [ *Visual Studio SDK 安裝路徑*\VisualStudioIntegration\Tools\Bin\] 資料夾，然後輸入：

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
> 字元- (虛線) 和/ (正斜線) 都可接受表示命令列參數的標記法。

 可接受的旗標，以及它們的意義，如下所示。

|Switch|描述|
|------------|-----------------|
|-d|指定任何其他定義的符號。|
|-I|指出解析檔案參考時應該使用的其他 include 路徑。|
|-l|指定 <xref:System.Globalization.CultureInfo> 文化特性名稱，例如 "en-us"。|
|-E|發出命令專案的指定命名空間中的 c # 物件，後面接著 [C&#124;H&#124;N]：*filename*，其中 C = c #，H = c + + 標頭，N = 命名空間。 C # 需要命名空間。|
|-v|詳細資訊輸出。|

 -L 參數會指示編譯器選取一組字串，以產生對應至指定文化特性名稱的 cto 檔案 <xref:System.Globalization.CultureInfo> 。 指定的文化特性名稱應該符合 .vsct 檔案中一個或多個 [字串元素](../../extensibility/strings-element.md) 的 Language 屬性。 如果字串元素沒有 Language 屬性，則會繼承自包含的 [CommandTable](../../extensibility/commandtable-element.md)專案。

 .Vsct 檔案可以有多個字串元素，而且每個專案都有不同的語言屬性。 全球化是藉由多次執行 .VSCT 編譯器並變更每個文化特性名稱的-L 參數來達成。

 如果-L 參數指定的文化特性名稱與任何字串專案的 Language 屬性不相符，則編譯器會嘗試比對語言，而不是區域。 例如，如果找不到 "en-us"，編譯器會改為嘗試 "en"。 若失敗，將會嘗試作業系統目前的文化特性。 若失敗，將會編譯它所找到的第一個字串元素。

 -E 參數可以用來發出包含命令表格所使用之符號的 C 樣式標頭檔，或發出包含命令符號物件的 c # 檔案。

 -D 和-I 參數具有具有相同名稱之 Cl.exe C 預處理器旗標的語法。 -D 格式為 X = Y 的定義用於擴充屬性中的 XML 架構 \<Defined> 測試 `Condition` 。 -I 包含路徑可用來解析 \<Include> 和檔案 \<Extern> \<Bitmap> 參考。 如需詳細資訊，請參閱 [.VSCT XML 架構參考](../../extensibility/vsct-xml-schema-reference.md)。

 .VSCT 編譯器也可以反編譯先前建立的二進位檔案。 若要這樣做，請提供的二進位檔案 \<infile> 。   如果二進位檔案是由 .VSCT 編譯器所產生，它的符號已經內嵌，而且會在輸出的區段中產生具有符號名稱的輸出 \<Symbols> 。 如果二進位檔是由 .CTC 編譯器所產生，則輸出會包含實際的 Guid 和識別碼。 如果 Ctc.exe 目前版本所產生的 *. .ctsym 檔案與二進位輸入檔案位於相同的資料夾中，則會從該檔案載入符號並用於輸出。

## <a name="see-also"></a>另請參閱
- [Visual Studio 命令表檔案 (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT XML 結構描述參考](../../extensibility/vsct-xml-schema-reference.md)
- [VSPackage 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
