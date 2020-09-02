---
title: 獨立模式 Shell 應用程式的服務指導方針 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Shell integrated mode, serviceability
- Shell integrated mode [Visual Studio], serviceability
ms.assetid: 747d1a47-b8b3-4e8b-93c0-768724be48f2
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 093690c293ff6857eedc50d5eccc793d7d5bb114
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159266"
---
# <a name="servicing-guidelines-for-isolated-shell-applications"></a>獨立模式 Shell 應用程式的服務方針
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當您散發 Visual Studio 的獨立模式 shell 應用程式時，您必須能夠在安裝應用程式之後，提供軟體更新。 若要這樣做，您必須使用 Microsoft Installer (MSI) 檔來安裝您的應用程式。 這種安裝可讓您的客戶在不需自訂介入的情況下，由 Web 下載並使用 Microsoft 提供的軟體更新。  
  
## <a name="servicing-requirements"></a>服務需求  
 您可以確定您的安裝程式符合下列三個準則，以確定您的隔離式 shell 安裝可以允許更新。  
  
### <a name="redistribute-by-using-an-msi"></a>使用 MSI 重新發佈  
 您必須使用 MSI 來轉散發應用程式，因為 MSI 會保留產品身分識別，並確定應用程式在用戶端電腦上具有實體位置。 合併模組 ( .msm 檔案) 不提供這類保證，也不應該使用。  
  
### <a name="accounting-for-custom-actions"></a>自訂動作的帳戶處理  
 自訂動作是安裝程式中非標準的安裝指示詞。 自訂動作會變更檔案位置、登錄設定、使用者設定或其他安裝專案等參數。 自訂動作可能會在安裝時處理資料。  
  
 當您在安裝程式中使用自訂動作時，您必須確定每個安裝時間自訂動作都必須有對應的自訂動作，才能在使用者卸載應用程式時復原動作。 如果您的安裝程式無法提供對應的卸載自訂動作，移除您的應用程式會讓它保持部分安裝。  
  
- 當軟體更新變更這些版本或雜湊值時，依賴特定檔案版本或雜湊值的自訂動作將會失敗。 在此情況下，您的自訂動作必須手動更新這些值。 如果產品版本之間共用檔案或雜湊值的版本，就會發生其他問題。 請盡可能避免這種相依性。  
  
### <a name="accounting-for-shared-files"></a>共用檔案的帳戶處理  
 共用的檔案具有相同的名稱，且會由多項產品安裝至相同的位置。 這些產品在版本、庫存單位 (SKU) 或兩者之間可能不同，而產品可以同時存在於指定的電腦上。 不過，共用檔案有許多原因會造成服務問題：  
  
- 更新共用檔案可能會導致應用程式相容性問題，因為某個應用程式的更新可能會變更第二個尚未更新的應用程式所使用的檔案版本。 共用檔案的產品安裝程式會計算共用檔案的參考。 因此，卸載產品並不會影響已安裝實例計數以外的共用檔案。  
  
- 快速修正工程 (QFE) 安裝程式會將檔案版本還原為 QFE 安裝程式所服務的產品版本。 此程式可能會中斷已傳遞更新共用檔案的應用程式。
