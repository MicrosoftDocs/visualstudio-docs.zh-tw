---
title: Code Analysis Policy Errors
ms.date: 11/04/2016
description: 瞭解 Visual Studio 中的程式碼分析原則錯誤。 如果簽入程式碼時不符合原則，就會顯示錯誤的描述。
ms.custom: SEO-VS-2020
ms.topic: reference
f1_keywords:
- vs.codeanalysis.policyfailures
helpviewer_keywords:
- policy errors, code analysis
ms.assetid: d1f221cd-68c0-4277-9397-b76ad0dbae77
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5fdd14b394bca495b38f408be94b46a4b9a68c01
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860551"
---
# <a name="code-analysis-policy-errors"></a>Code Analysis Policy Errors

如果未在簽入時滿足程式碼分析原則，就會發生下列錯誤：

**一或多個專案的程式碼分析設定與程式碼分析原則不相容。**

一或多個程式碼專案的程式碼分析需求籤入專案原始檔控制不符合。 此錯誤可能是由下列一或多個情況所造成：

- 方案中所有專案的組建都未啟用程式碼分析。

- 在 Visual Studio 中，專案的本機規則集所設定的 **動作** 設定較不嚴格，例如專案規則集，在伺服器上設定為 **動作** = **錯誤** 的規則，其 **動作** 設定為 [**警告**] 或 [**無**] 會在 Visual Studio) 中執行的規則集。

- Visual Studio 中指定的規則集未包含專案的程式碼分析簽入原則中指定的規則集內所指定的所有規則。

**程式碼分析原則失敗。專案中有錯誤， {0} 或組建不是最新狀態。**

組建中包含錯誤或修正了錯誤，但未在修正後執行程式碼分析。

**簽入失敗。程式碼分析原則要求您使用開啟的方案簽入 Visual Studio。**

程式碼分析原則要求所有簽入的檔案都必須位於目前開啟的方案中。 若要更正這個錯誤，請開啟包含要簽入之檔案的方案。

**並非暫止簽入中的所有檔案都在目前開啟的方案內。**

程式碼分析原則要求所有簽入的檔案都必須位於目前開啟的方案中。 當有開啟的解決方案時，就會引發此錯誤，但 [擱置簽入] 視圖中的某些檔案並不是目前開啟之方案的一部分。 若要更正這個錯誤，請開啟包含要簽入之檔案的方案。

**' ' 的版本 {0} 不正確。原則中指定的強式名稱是 ' {1} '。**

此錯誤適用于 .NET 專案。 程式碼分析原則所需的 rule 存在於本機電腦上，但版本/公開金鑰不相符。 若要更正此錯誤，原則建立者必須在其電腦上更新 *C:\Program Files\Microsoft Visual Studio 8 \ Team Tools\Static Analysis \\ Tools\FxCop\Rules* 目錄中的 .dll。

**{0}原則中指定的 ' ' 元件不存在。**

此錯誤適用于 .NET 專案。 程式碼分析原則所需的規則未在用戶端電腦上安裝對應的 dll。 若要更正此錯誤，原則建立者必須在其電腦上更新 *C:\Program Files\Microsoft Visual Studio 8 \ Team Tools\Static \\ Analysis Tools\FxCop\Rules* 目錄中的 dll。

**專案 {0} 規則設定不符合程式碼分析原則。**

此錯誤適用于 .NET 專案。 Managed 程式碼規則設定與原則所需的設定不嚴格。 若要更正此錯誤，用戶端設定必須與伺服器上的原則需求相同或更嚴格。

**使用中設定未啟用程式碼分析。 {0} 在簽入之前切換至設定和組建專案 {1} 。**

在中 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ，使用中的設定未啟用程式碼分析，但至少已啟用一個程式碼分析。

**簽入之前，您必須在專案屬性和組建中啟用 managed 二進位檔的程式碼分析 {0} 。**

此錯誤適用于 [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] .net 應用程式。 原則需要執行 managed 程式碼分析，但不會在用戶端上的目前專案中啟用。

**簽入之前，您必須在專案屬性和組建中啟用程式碼分析 {0} 。**

此錯誤適用于 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 專案和 Web 專案。 原則需要執行 managed 程式碼分析，但不會在用戶端上的目前專案中啟用。

**簽入之前，您必須在專案屬性和組建中啟用 C/c + + 程式碼分析 {0} 。**

此錯誤適用于未受管理的專案。 程式碼分析原則需要 C/c + + 的程式碼分析，但在用戶端的目前專案中未啟用。

## <a name="see-also"></a>另請參閱

- [程式碼分析應用程式錯誤](../code-quality/code-analysis-application-errors.md)
