---
title: 程式碼分析原則錯誤 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codeanalysis.policyfailures
helpviewer_keywords:
- policy errors, code analysis
ms.assetid: d1f221cd-68c0-4277-9397-b76ad0dbae77
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 268940f39d3d74e7dd701f9c458d7dd08ff6c1f7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="code-analysis-policy-errors"></a>程式碼分析原則錯誤
如果程式碼分析原則不符合在簽入時，會發生下列錯誤：  
  
 **一或多個專案的程式碼分析設定不相容的程式碼分析原則。**  
  
 針對一或多個程式碼專案不符合所簽入 team 專案的原始檔控制的程式碼分析需求。 這個錯誤可能被因一或多個下列條件：  
  
1.  在所有方案中專案的組建上未啟用程式碼分析。  
  
2.  設定 Visual Studio 的專案中有較不嚴格的本機規則**動作**設定 team 專案的規則，例如設定規則設為比**動作**=**錯誤**在伺服器上有其**動作**設**警告**或**無**規則集執行的 Visual Studio 中)。  
  
3.  設定 Visual Studio 中指定的規則不包含的所有規則規則集指定的程式碼分析簽入原則中的 team 專案中所指定。  
  
 **程式碼分析原則失敗。在專案 {0} 中有錯誤或組建不是最新狀態。**  
  
 可能是組建包含錯誤或已修正錯誤，而未在修正之後執行程式碼分析。  
  
 **簽入失敗。程式碼分析原則需要，請透過 Visual Studio 與開啟的方案。**  
  
 程式碼分析原則需要所簽入的所有檔案必須都位於目前開啟的方案。 若要更正這個錯誤，開啟方案，其中包含要簽入的檔案。  
  
 **暫止簽入中不是所有檔案都都位於目前開啟的方案中。**  
  
 程式碼分析原則需要所簽入的所有檔案必須都位於目前開啟的方案。 開啟的方案，但 「 擱置中的檢查 」 檢視中的某些檔案並不屬於目前開啟的方案時，會引發此錯誤。 若要更正這個錯誤，開啟方案，其中包含要簽入的檔案。  
  
 **'{0}' 的版本不正確。強式名稱的原則中指定為 '{1}'。**  
  
 此錯誤適用於.NET 專案。 程式碼分析原則所需的規則.dll 存在於本機電腦，但版本/公開金鑰不符。 若要更正這個錯誤，原則建立者必須更新中的 dll *C:\Program Files\Microsoft Visual Studio 8\Team Tools\Static Analysis Tools\FxCop\Rules\\* 其電腦上的目錄。  
  
 **'{0}' 的原則中指定組件不存在。**  
  
 此錯誤適用於.NET 專案。 程式碼分析原則所需的規則沒有對應的用戶端電腦上安裝的 dll。 若要更正這個錯誤，原則建立者必須更新的 dll 中*C:\Program Files\Microsoft Visual Studio 8\Team Tools\Static Analysis Tools\FxCop\Rules\\* 其電腦上的目錄。  
  
 **專案 {0} 規則設定不是與程式碼分析原則一致。**  
  
 此錯誤適用於.NET 專案。 無法為嚴格的原則要求必須為 managed 程式碼規則設定。 若要更正這個錯誤，用戶端設定必須是相同或比在伺服器上原則的需求更嚴格。  
  
 **使用中的設定未啟用程式碼分析。切換至組態 {0} 並建置專案 {1} 簽入之前。**  
  
 在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、 使用中的組態並沒有啟用，程式碼分析，但沒有啟用至少一個程式碼分析。  
  
 **您必須啟用程式碼分析專案 {0} 屬性中的 managed 二進位檔，並在簽入之前建置。**  
  
 發生這個錯誤[!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)].NET 應用程式。 原則需要 managed 程式碼分析來執行，但它不會啟用用戶端上目前專案中。  
  
 **您必須啟用專案 {0} 屬性中的程式碼分析，並在簽入之前建置。**  
  
 套用至這個錯誤[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]專案和 Web 專案。 原則需要 managed 程式碼分析來執行，但它不會啟用用戶端上目前專案中。  
  
 **您必須在專案 {0} 屬性中啟用 C/c + + 程式碼分析，並建置在簽入之前。**  
  
 此錯誤適用於 unmanaged 的專案。 程式碼分析原則需要程式碼分析 C/c + +，但是未啟用用戶端上目前專案中。  
  
## <a name="see-also"></a>請參閱  
 [程式碼分析應用程式錯誤](../code-quality/code-analysis-application-errors.md)