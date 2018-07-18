---
title: VSCT 編譯器命令列的旗標 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6e2e1045adb451c7f4dd06b888fca356d26b7ff3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31139769"
---
# <a name="vsct-compiler-command-line-flags"></a>VSCT 編譯器命令列的旗標
Visual Studio 命令表 (VSCT) 編譯器會提供命令列參數，以確保成功編譯的.vsct 檔案。  
  
## <a name="command-line-parameters"></a>命令列參數  
 若要檢視從基本的 VSCT 說明[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]**命令**視窗中，瀏覽至*Visual Studio SDK 安裝路徑*\VisualStudioIntegration\Tools\Bin\ 資料夾，並輸入：  
  
```  
vsct /?  
```  
  
 這會傳回：  
  
```  
Microsoft (R) Visual Studio (R) Command Table Compiler Version 3.00.2000  
  
Syntax: vsct <infile> [<outfile>] [-S[symbols file]] [-D<preprocessor-define>]*  
[-I<include-path>]* [-L<language>] [-E[C|H|N]:<name>]  
  
  -D    Specify any additional preprocessor defines  
  -I    Indcate what additional include paths to send to the preprocessor  
  -L    Specify the langauge to use when selecting strings  
  -E    Emit C# objects in the specified namespace for command items,  
        folowed by [L|F|H|N]:<value>  
        F = Name of the file to emit (used if -EL is provided)  
        L = Name of a language providing a CodeDOM provider  
        N = namespace (required if -EL is provided)  
        H = C++ header  
  -c    Clean build skipping dependancy checks  
  -v    Verbose output  
```  
  
> [!NOTE]
>  字元-（虛線） 和 / （斜線） 是兩個可接受的標記法來表示命令列參數。  
  
 可接受的旗標，它們代表什麼意思是，如下所示。  
  
|參數|描述|  
|------------|-----------------|  
|-D|指定任何其他已定義的符號。|  
|-I|表示額外的 include 解析檔案參考時，應使用的路徑。|  
|-L|指定<xref:System.Globalization.CultureInfo>文化特性名稱，例如"EN-US"。|  
|-E|發出命令項目，後面加上指定的命名空間中的 C# 物件 [C&#124;H&#124;N]:*filename*，C = C#，H = c + + 標頭，N = 命名空間。 需要 C# 命名空間。|  
|-v|詳細資訊輸出。|  
  
 -L 參數會指示編譯器選取一組的字串，以產生二進位.cto 檔對應到給定<xref:System.Globalization.CultureInfo>文化特性名稱。 指定的文化特性名稱應符合一或多個語言屬性[字串項目](../../extensibility/strings-element.md).vsct 檔中。 如果字串項目不有任何語言屬性時，它會繼承包含[CommandTable 元素](../../extensibility/commandtable-element.md)。  
  
 .Vsct 檔可能有多個字串元素，而且每個可能具有不同的語言屬性。 全球化是多次執行 VSCT 編譯器，以及變更每個文化特性名稱-L 參數來達成的。  
  
 如果-L 參數所指定的文化特性名稱不符合任何字串項目的 Language 屬性，編譯器會嘗試使其符合語言，與非區域。 例如，如果找不到"EN-US"，編譯器會嘗試"en"改為。 如果無法做到，將會嘗試目前的文化特性的作業系統。 失敗，它將會編譯它找到的第一個字串項目。  
  
 -E 參數可用來發出 c-style 標頭檔，其中包含命令表中，所使用的符號，或發出 C# 檔，其中包含命令符號的物件。  
  
 -D 和-I 參數具有 Cl.exe C 前置處理器旗標，具有相同名稱的語法。 -D X = Y 格式的定義會用於擴充的 XML 架構\<定義 > 測試`Condition`屬性。 -I include 路徑用來解析\<Include >， \<Extern > 和\<點陣圖 > 檔案參考。 如需詳細資訊，請參閱[VSCT XML 結構描述參考](../../extensibility/vsct-xml-schema-reference.md)。  
  
 VSCT 編譯器也可以反編譯先前建置的二進位檔案。 若要這樣做，請提供 二進位檔\<infile >。   如果 VSCT 編譯器所產生的二進位檔案，它會有其已內嵌的符號，並會產生輸出中的符號名稱\<符號 > 一節的輸出。 如果二進位檔由 CTC 編譯器所產生，則輸出會包含實際的 Guid 和 Id。 產生目前版本的 Ctc.exe *.ctsym 檔案是否為二進位的輸入檔的相同資料夾中，會從該檔案載入符號，與用於輸出。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令表 (。Vsct) 檔案](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT XML 結構描述參考](../../extensibility/vsct-xml-schema-reference.md)   
 [VSPackage 如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)