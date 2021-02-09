---
title: Configuring Warnings in Visual Basic
description: 瞭解如何在 Visual Basic 中設定警告，進而協助您以較少的 bug 來撰寫更簡潔、更快速、更好的程式碼。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Basic], warnings
- run-time errors, warnings
- warnings, configuring
ms.assetid: 99cf4781-bd4d-47b4-91b9-217933509f82
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a59ee0e3aed10b5fd48fcbf57d9cb69aca3f929e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907640"
---
# <a name="configuring-warnings-in-visual-basic"></a>在 Visual Basic 中設定警告

[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 編譯器會包含一組警告，這組警告與可能會造成執行階段錯誤的程式碼有關。 您可以使用該項資訊，來撰寫更簡潔、更快速、更好且錯誤更少的程式碼。 例如，當使用者嘗試叫用未指派之物件變數的成員時、從未設定傳回值的函式傳回時，或執行 `Try` 區塊但攔截例外狀況的邏輯有錯誤時，編譯器就會產生警告。

編譯器有時會替使用者提供額外的邏輯，讓使用者能將重心放在手邊的工作，而不是放在預期可能的錯誤。 在舊版的 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中，**Option Strict** 是用於限制 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 編譯器所提供的額外邏輯。 設定警告可讓您在個別警告層級上，以更細微的方式限制這個邏輯。

您可能會想要自訂專案，關閉與應用程式無關的某些警告，並將其他警告變成錯誤。 本頁將說明如何開啟和關閉個別警告。

## <a name="turning-warnings-off-and-on"></a>開啟和關閉警告
設定警告的方法有兩種：您可以使用 [專案設計工具] 加以設定，也可以使用 **/warnaserror** 和 **/nowarn** 編譯器選項。

[專案設計工具] 頁面的 [編譯] 索引標籤可供您開啟和關閉警告。 選取 [停用所有警告] 核取方塊即可停用所有警告，而選取 [將所有警告視為錯誤] 則會將所有警告視為錯誤。 有些個別警告還能在顯示的表格中，視需要切換為錯誤或警告。

當 [Option Strict] 設定為 [Off] 時，就不能將 [Option Strict] 相關的警告視為彼此獨立。 當 [Option Strict] 設定為 [On] 時，則不論關聯之警告的狀態為何，都會視為錯誤。 在命令列編譯器中指定 `/optionstrict:custom` 即可將 [Option Strict] 設定為 [Custom]，此時可以單獨開啟或關閉 [Option Strict] 警告。

編譯器的 **/warnaserror** 命令列選項也能用於指定是否要將警告視為錯誤。 您可以將逗號分隔清單新增至此選項，利用 + 或 - 指定應將哪些警告視為錯誤或警告。 下表詳細說明可能的選項。

|命令列選項|指定|
| - |---------------|
|`/warnaserror+`|將所有警告視為錯誤|
|`/warnsaserror`-|不要將警告視為錯誤。 此為預設值。|
|`/warnaserror+:<warning list` `>`|將特定警告視為錯誤，這些警告會在逗號分隔清單中依其錯誤識別碼列出。|
|`/warnaserror-:<warning list>`|不要將特定警告視為錯誤，這些警告會在逗號分隔清單中依其錯誤識別碼列出。|
|`/nowarn`|不會報告警告。|
|`/nowarn:<warning list>`|不會報告特定警告，這些警告會在逗號分隔清單中依其錯誤識別碼列出。|

警告清單包含應視為錯誤之警告的錯誤識別碼，可搭配命令列選項用來開啟或關閉特定警告。 如果警告清單包含無效的號碼，則會報告錯誤。

## <a name="examples"></a>範例
下表提供命令列引數範例，並描述每個引數的功能。

|引數|描述|
|--------------|-----------------|
|`vbc /warnaserror`|指定應該將所有警告視為錯誤。|
|`vbc /warnaserror:42024`|指定應該將警告 42024 視為錯誤。|
|`vbc /warnaserror:42024,42025`|指定應該將警告 42024 和 42025 視為錯誤。|
|`vbc /nowarn`|指定不應該報告任何警告。|
|`vbc /nowarn:42024`|指定不應該報告警告 42024。|
|`vbc /nowarn:42024,42025`|指定不應該報告警告 42024 和 42025。|

## <a name="types-of-warnings"></a>警告類型
以下是您可能需視為錯誤的警告清單。

### <a name="implicit-conversion-warning"></a>隱含轉換的警告
當出現隱含轉換時，就會產生此警告。 不包括使用 `&` 運算子從內建數值類型隱含轉換成字串。 新專案的預設值為關閉。

識別碼：42016

### <a name="late-bound-method-invocation-and-overload-resolution-warning"></a>晚期繫結方法引動過程和多載解析的警告
當出現晚期繫結時，就會產生此警告。 新專案的預設值為關閉。

識別碼︰42017

### <a name="operands-of-type-object-warnings"></a>'Object' 類型運算元的警告
當出現 `Object` 類型的運算元時，就會產生此警告，在 [Option Strict 為 On] 的情況下會發生錯誤。 新專案的預設值為開啟。

識別碼︰42018 和 42019

### <a name="declarations-require-as-clause-warnings"></a>宣告需要 'As' 子句的警告
當變數、函式或屬性宣告缺少 `As` 子句時，就會產生此警告，在 [Option Strict 為 On] 的情況下會發生錯誤。 未指派類型的變數會假設為 `Object` 類型。 新專案的預設值為開啟。

識別碼︰42020 (變數宣告)、42021 (函式宣告) 和 42022 (屬性宣告)。

### <a name="possible-null-reference-exception-warnings"></a>可能發生 Null 參考例外狀況的警告
當變數在未指派值前便已使用時，就會產生此警告。 新專案的預設值為開啟。

識別碼：42104、42030

### <a name="unused-local-variable-warning"></a>未使用區域變數的警告
當宣告了某個區域變數但從未參考到此變數時，就會產生此警告。 預設值為開啟。

識別碼︰42024

### <a name="access-of-shared-member-through-instance-variable-warning"></a>透過執行個體變數存取共用成員的警告
當透過可能有副作用的執行個體存取共用成員時，或是當透過不在運算式右邊或當作參數傳入的執行個體變數存取共用成員時，就會產生此警告。 新專案的預設值為開啟。

識別碼︰42025

### <a name="recursive-operator-or-property-access-warnings"></a>遞迴運算子或屬性存取的警告
當常式的主體所使用的運算子或屬性是用來定義它的相同運算子或屬性時，就會產生此警告。 新專案的預設值為開啟。

識別碼：42004 (運算子)、42026 (屬性)

### <a name="function-or-operator-without-return-value-warning"></a>函式或運算子沒有傳回值的警告
當函式或運算子未指定傳回值時，就會產生此警告。 對與函式同名的隱含區域變數省略 `Set` 的情形也包含在內。 新專案的預設值為開啟。

識別碼：42105 (函式)、42016 (運算子)

### <a name="overloads-modifier-used-in-a-module-warning"></a>Overloads 修飾詞用於模組的警告
當 `Overloads` 用於`Module`時，就會產生此警告。 新專案的預設值為開啟。

識別碼︰42028

### <a name="duplicate-or-overlapping-catch-blocks-warnings"></a>Catch 區塊重複或重疊的警告
當 `Catch` 區塊由於未定義與其他 `Catch` 區塊的關聯而從未到達時，就會產生此警告。 新專案的預設值為開啟。

識別碼：42029、42031

## <a name="see-also"></a>另請參閱

- [錯誤類型](/dotnet/visual-basic/programming-guide/language-features/error-types)
- [嘗試。。。抓住。。。Finally 語句](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)
- [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn)
- [/warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror)
- [編譯頁面、專案設計工具 (Visual Basic) ](../ide/reference/compile-page-project-designer-visual-basic.md)
- [預設為關閉的編譯器警告](/cpp/preprocessor/compiler-warnings-that-are-off-by-default)
