---
title: 程式碼分析原則錯誤 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.policyfailures
helpviewer_keywords:
- policy errors, code analysis
ms.assetid: d1f221cd-68c0-4277-9397-b76ad0dbae77
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8cb50fffc1411e77f771b0f74fbb947144eb6017
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672915"
---
# <a name="code-analysis-policy-errors"></a>程式碼分析原則錯誤
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如果在簽入時未滿足程式碼分析原則，就會發生下列錯誤：

 **一或多個專案的程式碼分析設定與程式碼分析原則不相容。**

 一或多個程式碼專案不符合 team 專案原始檔控制的程式碼分析需求。 此錯誤可能是由下列一或多個狀況所造成：

1. 方案中所有專案的組建都未啟用程式碼分析。

2. Visual Studio 中專案的本機規則集具有比 team 專案規則集更嚴格的**動作**設定，例如，在伺服器上設定為**動作**=**錯誤**的規則，其**動作**設定為 [**警告**]或**None**在 Visual Studio 中執行的規則集內）。

3. 在 Visual Studio 中指定的規則集不包含 team 專案的程式碼分析簽入原則中指定的規則集內所指定的所有規則。

   **程式碼分析原則失敗。專案 {0} 中有錯誤，或組建不是最新狀態。**

   可能是組建包含錯誤或已修正錯誤，但未在修正之後執行程式碼分析。

   **簽入失敗。程式碼分析原則會要求您使用開啟的方案，透過 Visual Studio 簽入。**

   程式碼分析原則會要求所有簽入的檔案都必須在目前開啟的方案中。 若要更正此錯誤，請開啟包含要簽入之檔案的方案。

   **並非暫止簽入中的所有檔案都是在目前開啟的方案中。**

   程式碼分析原則會要求所有簽入的檔案都必須在目前開啟的方案中。 當有開啟的方案時，就會引發此錯誤，但 [暫止簽入] 視圖中的某些檔案並不是目前開啟之方案的一部分。 若要更正此錯誤，請開啟包含要簽入之檔案的方案。

   **' @No__t_1 ' 的版本不正確。原則中指定的強式名稱是 ' {1} '。**

   此錯誤適用于 .NET 專案。 本機電腦上有程式碼分析原則所需的規則 .dll，但版本/公開金鑰不相符。 若要更正此錯誤，原則建立者必須在其電腦上更新*C:\Program Files\Microsoft Visual Studio 8 \ Team Tools\Static Analysis Tools\FxCop\Rules \\* 目錄中的 .dll。

   **原則中指定的 ' {0} ' 元件不存在。**

   此錯誤適用于 .NET 專案。 程式碼分析原則所需的規則不會在用戶端電腦上安裝對應的 dll。 若要更正此錯誤，原則建立者必須在其電腦上更新*C:\Program Files\Microsoft Visual Studio 8 \ Team Tools\Static Analysis Tools\FxCop\Rules \\* 目錄中的 dll。

   **專案 {0} 規則設定不符合程式碼分析原則。**

   此錯誤適用于 .NET 專案。 Managed 程式碼規則設定不像原則所需的嚴格。 若要更正此錯誤，用戶端設定必須與伺服器上的原則需求相同或更嚴格。

   **使用中設定時，未啟用程式碼分析。在簽入之前，切換到設定 {0} 和組建專案 {1}。**

   在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中，使用中的設定未啟用程式碼分析，但至少有一個已啟用的程式碼分析。

   **在簽入之前，您必須在專案 {0} 屬性和組建中啟用受控二進位檔的程式碼分析。**

   此錯誤適用于 [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] .NET 應用程式。 原則需要執行 managed 程式碼分析，但不會在用戶端上的目前專案中啟用。

   **在簽入之前，您必須在專案 {0} 屬性和組建中啟用程式碼分析。**

   這個錯誤適用于 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 專案和 Web 專案。 原則需要執行 managed 程式碼分析，但不會在用戶端上的目前專案中啟用。

   **在簽入之前，C++您必須在專案 {0} 屬性和組建中啟用 C/程式碼分析。**

   此錯誤適用于非受控專案。 程式碼分析原則需要 C/C++的程式碼分析，但不會在用戶端上的目前專案中啟用。

## <a name="see-also"></a>請參閱
 [程式碼分析應用程式錯誤](../code-quality/code-analysis-application-errors.md)
