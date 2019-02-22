---
title: 程式碼分析原則錯誤
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.policyfailures
helpviewer_keywords:
- policy errors, code analysis
ms.assetid: d1f221cd-68c0-4277-9397-b76ad0dbae77
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 103a48172665875c3615ce57b90dc77beeb6b5c4
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55921558"
---
# <a name="code-analysis-policy-errors"></a>程式碼分析原則錯誤

如果程式碼分析原則不符合在簽入時，就會發生下列錯誤：

**一或多個專案的程式碼分析設定與不相容的程式碼分析原則。**

簽入至原始檔控制專案的程式碼分析需求不符合一或多個程式碼專案。 此錯誤可能被因一或多個下列條件：

- 所有的方案中專案的組建上未啟用程式碼分析。

- 本機設定 Visual Studio 中的專案有較不嚴格的規則**動作**設定專案的規則，例如設定規則，設定為比**動作**=**錯誤**在伺服器上有其**動作**設定為**警告**或是**無**規則集 Visual Studio 中正在執行中)。

- 設定 Visual Studio 中所指定的規則不包含的所有規則規則集指定的程式碼分析簽入原則中的專案中所指定。

**程式碼分析原則失敗。在專案中有錯誤{0}或組建不是最新狀態。**

建置包含錯誤或已修正錯誤，但在修正後並未執行，程式碼分析。

**簽入失敗。程式碼分析原則需要，請透過 Visual Studio 與開啟的方案。**

程式碼分析原則需要簽入的所有檔案必須都位於目前開啟的方案。 若要更正這個錯誤，開啟包含簽入檔案的方案。

**並非所有暫止簽入中的檔案是在目前開啟的方案。**

程式碼分析原則需要簽入的所有檔案必須都位於目前開啟的方案。 當沒有開啟的方案，但 「 擱置中的檢查 」 檢視中的某些檔案並不屬於目前開啟的方案時，會引發此錯誤。 若要更正這個錯誤，開啟包含簽入檔案的方案。

**版本 '{0}' 不正確。強式名稱的原則中指定是 '{1}'。**

此錯誤適用於.NET 專案。 所需的程式碼分析原則規則.dll 存在於本機電腦，但版本/公用金鑰不相符。 若要更正這個錯誤，原則建立者必須更新 \static *C:\Program Files\Microsoft Visual Studio 8\Team Tools\Static Analysis Tools\FxCop\Rules\\* 目錄在其電腦上。

**'{0}' 原則中指定的組件不存在。**

此錯誤適用於.NET 專案。 程式碼分析原則所需的規則沒有相對應的 dll 安裝在用戶端電腦上。 若要更正這個錯誤，原則建立者必須更新在 dll *C:\Program Files\Microsoft Visual Studio 8\Team Tools\Static Analysis Tools\FxCop\Rules\\* 目錄在其電腦上。

**專案{0}規則設定不是使用程式碼分析原則的合規性。**

此錯誤適用於.NET 專案。 Managed 程式碼規則設定不嚴格的原則要求。 若要更正這個錯誤，用戶端設定必須是相同或比在伺服器上的原則需求。

**使用中的組態未啟用程式碼分析。切換至組態{0}並建置專案{1}簽入之前。**

在  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、 使用中的組態並沒有啟用，程式碼分析，但沒有啟用的至少一個程式碼分析。

**您必須啟用程式碼分析專案中的受控二進位檔{0}屬性和簽入之前的組建。**

此錯誤適用於[!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)].NET 應用程式。 原則會要求要執行的 managed 程式碼分析，但未啟用用戶端上目前的專案中。

**您必須啟用專案中的程式碼分析{0}屬性和簽入之前的組建。**

套用至這個錯誤[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]專案和 web 專案。 原則會要求要執行的 managed 程式碼分析，但未啟用用戶端上目前的專案中。

**您必須在專案中啟用 C/c + + 程式碼分析{0}屬性和簽入之前的組建。**

此錯誤適用於非受控專案。 程式碼分析原則需要程式碼分析 C/c + +，但未啟用用戶端上目前的專案中。

## <a name="see-also"></a>另請參閱

- [程式碼分析應用程式錯誤](../code-quality/code-analysis-application-errors.md)