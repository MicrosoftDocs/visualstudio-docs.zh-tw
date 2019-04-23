---
title: 編輯後繼續在 Visual Basic 中的不支援的編輯 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
helpviewer_keywords:
- Edit and Continue [Visual Basic], unsupported method and property body edits
ms.assetid: 9b8fdc41-a193-49ad-ad72-dfcadd46f4b3
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 94a151a7adab5c8246cec38c2e62d76788beb6e7
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60076937"
---
# <a name="unsupported-edits-in-visual-basic-edit-and-continue"></a>Visual Basic 編輯後繼續中不支援的編輯
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[編輯後繼續] 可讓您在中斷模式停止程式執行、變更執行中的程式碼，然後以新加入的變更繼續執行程式。 通常會禁止影響類別之公用結構的宣告式程式碼編輯，但是允許對類別內的方法、屬性主體或私用宣告進行多項編輯。  
  
 如果您必須進行任何不支援的變更，則必須先停止偵錯，進行變更，然後開始新的偵錯工作階段。  
  
### <a name="BKMK_MethodandPropertyBodyEdits"></a> 方法和屬性主體編輯  
 **不支援靜態區域變數變更**:新增或更新本機變數，或如果該移除靜態區域變數會導致編譯錯誤。  
  
 **不支援變更泛型**:不支援對泛型方法本身或泛型方法主體進行變更。 可以加入、刪除或變更泛型類型的具現化或對現有泛型方法的呼叫。  
  
 **其他不支援的變更**  
  
- 變更呼叫堆疊上方法的引動過程陳述式。  
  
- 當指令指標最後位於 `Try...Catch` 區塊或 `Catch` 區塊中時，加入 `Finally` 區塊。  
  
- 移除`Try...Catch`區塊中，當指令指標位於`Catch`區塊或`Finally`區塊。  
  
- 在目前指令指標前後加入 `Using` 區塊。  
  
- 在目前指令指標前後加入 `SynchLock` 區塊。  
  
### <a name="BKMK_AttributeEdits"></a> 屬性編輯  
 [編輯後繼續] 不支援修改屬性。 具體而言，[編輯後繼續] 不支援下列變更：  
  
- 定義、編輯或刪除屬性類別。  
  
- 加入屬性。  
  
- 編輯或移除現有的屬性。  
  
### <a name="BKMK_ClassDeclarationEdits"></a> 類別宣告編輯  
 處於中斷模式時，[編輯後繼續] 不允許對類別宣告進行的大多數變更。 具體而言，[編輯後繼續] 不支援下列變更：  
  
- 重新命名、刪除或變更現有類別的繼承。  
  
- 實作新介面，或移除介面的實作。  
  
- 變更類別的修飾詞。  
  
- 加入、變更或移除 `ComClass` 狀態。  
  
- 編輯任何泛型類別宣告。  
  
### <a name="BKMK_ClassMemberDeclarationEdits"></a> 類別成員宣告編輯  
 大部分 [編輯後繼續] 案例中都禁止對成員宣告進行變更。 例如，您無法變更成員的簽章或存取層級，且如果完全移除成員可能會導致編譯錯誤，您就無法完全將其加以移除。 具體而言，[編輯後繼續] 不支援下列變更：  
  
- 在包含區塊中宣告相同名稱的全域或成員變數，以遮蔽現有成員變數。  
  
- 在區塊內宣告新的執行個體，以遮蔽靜態區域變數。  
  
- 移除事件的處理常式。 允許加入事件處理常式。  
  
- 加入新的多載屬性或方法，除非該屬性或方法是 `Private`，而且在任何使用中陳述式內都未出現該名稱。  
  
- 加入或移除成員變數上的 `WithEvents` 子句。  
  
- 刪除成員。  
  
- 變更屬性或方法宣告，以停止實作介面。  
  
- 編輯任何使用泛型的方法。  
  
- 變更非私用屬性或方法的簽章或傳回類型。  
  
- 覆寫或遮蔽基底類別中的成員。  
  
- 在標記為 `SequentialLayout` 或 `ExplicitLayout` 的任何類別中加入新的欄位。  
  
- 變更方法的 `MustInherit` 或 `NotOverridable` 狀態。  
  
- 變更屬性或方法的存取修飾詞。  
  
- 變更欄位的類型或唯讀狀態。  
  
- 變更公用欄位。  
  
### <a name="BKMK_CompilerOptionEdits"></a> 編譯器選項編輯  
 在中斷模式下使用 [編輯後繼續] 時，您無法變更、加入或移除下列編譯器選項：  
  
- **Option Strict**  
  
- **Option Explicit**  
  
- **Option Compare**  
  
### <a name="BKMK_ConstantsEdits"></a> 常數編輯  
 處於 [編輯後繼續] 模式時，對於常數的變更會受到嚴格的限制。 具體而言，[編輯後繼續] 不支援下列變更：  
  
- 加入或更新常數變數。  
  
- 變更常數的類型或值。  
  
- 移除常數。  
  
### <a name="BKMK_DelegateandEventDeclarationEdits"></a> 委派和事件宣告編輯  
 處於中斷模式時，[編輯後繼續] 不允許對委派和事件的某些變更。 具體而言，[編輯後繼續] 不支援下列變更：  
  
- 變更或刪除委派定義。  
  
- 刪除事件。  
  
### <a name="BKMK_EnumerationEdits"></a> 列舉編輯  
 在中斷模式期間，[編輯後繼續] 不允許對列舉 (`Enums`) 進行變更。 具體而言，[編輯後繼續] 不支援下列變更：  
  
- 修改 `Enum` 的基礎類型。  
  
- 加入、變更或移除 `Enum` 成員。  
  
- 變更 `Enum` 的存取修飾詞。  
  
### <a name="BKMK_ExternalDeclarationsEdits"></a> 外部宣告編輯  
 一般來說，您無法在 [編輯後繼續] 期間變更外部方法的宣告。 具體而言，[編輯後繼續] 不支援下列變更：  
  
- 加入或移除外部宣告。  
  
- 變更外部宣告的簽章或封送處理屬性。  
  
### <a name="BKMK_ImportsEdits"></a> 匯入編輯  
 處於中斷模式時，[編輯後繼續] 不允許加入、變更或移除 `Imports` 陳述式。  
  
### <a name="BKMK_InterfaceDefinitionEdits"></a> 介面定義編輯  
 雖然 [編輯後繼續] 可讓您經常變更實作介面的成員，但通常不允許變更實際介面定義。 具體而言，[編輯後繼續] 不支援下列變更：  
  
- 加入、變更或移除介面成員。  
  
- 刪除現有的介面。  
  
- 變更介面的存取修飾詞。  
  
- 變更介面繼承階層。  
  
### <a name="BKMK_ModuleDeclarationEdits"></a> 模組宣告編輯  
 處於中斷模式時，[編輯後繼續] 不允許對模組宣告進行的大多數變更。 具體而言，[編輯後繼續] 不支援下列變更：  
  
- 建立新的模組。  
  
- 重新命名或刪除現有的模組。  
  
- 變更模組的存取修飾詞。  
  
### <a name="BKMK_ModuleMemberDeclarationEdits"></a> 模組成員宣告編輯  
 使用 [編輯後繼續] 可讓您在中斷模式下，對模組成員 (例如屬性、方法和欄位) 進行各種變更。 不過，有些變更並不支援。 最值得注意的是，[編輯後繼續] 不支援加入、刪除或變更任何成員的類型或簽章。  
  
 具體而言，[編輯後繼續] 不支援下列變更：  
  
- 加入新成員，除非在任何使用中陳述式內都未出現該名稱。  
  
- 移除屬性或方法。  
  
- 變更屬性或方法的簽章。  
  
- 加入、重新命名、移動或刪除欄位。  
  
- 編輯任何使用泛型的方法。  
  
- 變更屬性或方法的存取修飾詞 (例如，將 `Public` 變更為 `Private`)。  
  
- 刪除或變更現有欄位的類型。  
  
### <a name="BKMK_NestedTypeDeclarationEdits"></a> 巢狀的類型宣告編輯  
 [編輯後繼續] 不支援將巢狀類型移至另一個命名空間或類型。  
  
### <a name="BKMK_StructureDeclarationEdits"></a> 結構宣告編輯  
 編輯後繼續時中的不允許大部分的變更，結構宣告**中斷**模式。 具體而言，[編輯後繼續] 不支援下列變更：  
  
- 重新命名或刪除現有的結構。  
  
- 實作新介面，或移除介面的實作。  
  
- 變更結構的存取修飾詞。  
  
### <a name="BKMK_StructureMemberDeclarationEdits"></a> 結構成員宣告編輯  
 使用 [編輯後繼續] 可讓您在中斷模式下，對結構成員 (屬性、方法和欄位) 進行各種變更。 不過，某些變更並不支援，尤其是會影響結構成員宣告的變更。 具體而言，[編輯後繼續] 不支援下列變更：  
  
- 移除屬性或方法。  
  
- 加入或移除欄位。  
  
- 變更屬性或方法的簽章。  
  
- 編輯任何使用泛型的方法。  
  
- 對屬性或方法宣告實作介面的狀態進行變更。  
  
- 變更屬性或方法的存取修飾詞 (例如，變更`Public`要**私人**)。  
  
- 移除欄位。  
  
- 變更欄位類型。  
  
## <a name="see-also"></a>另請參閱  
 [如何：套用在中斷模式中的編輯，以編輯後繼續](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)   
 [編輯後繼續 (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)
