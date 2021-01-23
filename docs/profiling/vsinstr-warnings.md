---
title: VSInstr 警告 | Microsoft Docs
ms.date: 11/04/2016
description: 瞭解 VSInstr.exe 工具發出的警告，以及您可以如何使用 NOWARN 選項以及警告號碼來抑制警告的出現。
ms.topic: reference
helpviewer_keywords:
- instrumentation, VSInstr tool
- warnings
- VSInstr tool
- warnings, VSInstr tool
- performance tools, VSInstr tool
ms.assetid: 47512bc9-a8e9-4628-883a-d9888edab786
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d5510c475ab566e65d2bd152136535fde62f257b
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98723123"
---
# <a name="vsinstr-warnings"></a>VSInstr 警告
下表列出 *VSInstr.exe* 工具所發出的警告。 若要隱藏警告訊息使其不出現，您可以使用 NOWARN 選項以及警告編號。

|警告編號|描述|
|--------------------|-----------------|
|**VSP1026**|不參考 MSCorLib 的程式庫不支援涵蓋範圍。 此情況常見於可攜式程式庫。<br /><br />[/EnableCodeCoverage](../test/vstest-console-options.md) 命令列選項是 .NET Core 的必要選項。|
|**VSP2000**|內部錯誤。 無法取得這個可執行檔的模組檔案名稱。|
|**VSP2001**|\<assembly name> 是強式名稱元件。 必須重新簽署後才能執行。<br /><br /> 檢測簽署的組件之後，就會發生這個警告。 您可以使用 *sn.exe* 工具來重新簽署二進位檔，或暫時關閉強式名稱需求。 如需詳細資訊，請參閱 [Sn.exe (強式名稱工具)](/dotnet/framework/tools/sn-exe-strong-name-tool)。|
|**VSP2002**|在檔案中找不到函式 \<funcname>\<filename><br /><br /> 如果在指定的檔案中找不到函式，就會發生這個警告。|
|**VSP2003**|在檔案中找不到函數的任何交叉跳躍 \<funcname> \<filename> 。<br /><br /> 如果 VSInstr 無法將交互跳躍點設為空值，就會發生這個警告。 交互跳躍點用於程式碼最佳化。|
|**VSP2004**|函 \<funcname> 式已使用 EXCLUDE 命令列參數來排除，但卻是必要的，因為它包含交叉跳躍點。<br /><br /> 如果函式已透過 EXCLUDE 選項排除，但在檢測程序期間需要此函式，就會發生這個警告。 分析工具會自動包含所需的函式。|
|**VSP2005**|內部檢測錯誤 \<error text><br /><br /> 如果無法執行檢測，則會發出這個警告。 檢閱錯誤文字以判斷是否可以修正。|
|**VSP2006**|找不到的 PDB \<name><br /><br /> 如果 PDB 檔案不存在於搜尋路徑上，或者不符合二進位檔，就會發生這個警告。|
|**VSP2007**|\<filename> 未包含任何 instrumentable 程式碼。<br /><br /> 如果二進位檔中的函式已全部排除，或者指定的檔案只包含資源，則會發出這個警告。|
|**VSP2008**|無法從取得安全性屬性 \<name> 。 錯誤碼 \<code><br /><br /> 如果使用者沒有 READ_DAC 權限，就會發生這個警告。 在檢測過程中，分析工具會嘗試保留二進位檔的原始 DACL。 因為新的二進位檔取代原始的二進位檔，原始二進位檔的 DACL 必須複製並套用至新的二進位檔。 如果使用者沒有原始二進位檔的 READ_DAC 存取權，這可能會失敗。|
|**VSP2009**|無法設定上的安全性屬性 \<name> 。 錯誤碼 \<error number><br /><br /> 如果使用者沒有 WRITE_DAC 權限，就會發生這個警告。 在檢測過程中，分析工具會嘗試保留二進位檔的原始 DACL。 因為新的二進位檔取代原始的二進位檔，原始二進位檔的 DACL 必須複製並套用至新的二進位檔。 如果使用者沒有新的二進位檔的 WRITE_DAC 存取權，這可能會失敗。|
|**VSP2010**|由於 -INCLUDE/-EXCLUDE 選項的緣故，未針對檢測選取任何函式|
|**VSP2011**|包含/排除 funcspec 不 \<name> 符合任何函數|
|**VSP2012**|映像未包含任何可對程式碼涵蓋範圍進行檢測的程式碼。<br /><br /> 分析工具不會檢測下列類型的程式碼︰<br /><br /> -   靜態 CRT 函式<br />-   使用 NonUserCodeAttribute 屬性化的 Managed 方法<br />-   使用 DebuggerHiddenAttribute 屬性化的 Managed 方法<br />-   MASM 區塊<br /><br /> 如果篩選之後沒有留下任何程式碼，則會產生此警告。|
|**VSP2013**|這個映像必須當做 32 位元處理序執行才能進行檢測。 已更新 CLR 標頭旗標以反映這種情況。<br /><br /> 分析工具可修改二進位檔，這樣一來 64 位元作業系統就可以在 WOW64 模擬器中開啟 32 位元處理序。 針對程式庫 (DLL)，如果它們在現有的 64 位元處理序中載入，這可能會失敗。 這個警告會通知使用者此相依性。|
|**VSP2014**|產生的已經過檢測的映像似乎無效，可能無法執行。<br /><br /> 當最後已經過檢測的組件具有無效的 PE 標頭時，會出現此訊息。|

## <a name="see-also"></a>另請參閱
- [VSInstr](../profiling/vsinstr.md)
