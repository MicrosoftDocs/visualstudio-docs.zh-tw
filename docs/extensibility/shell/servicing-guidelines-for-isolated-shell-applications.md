---
title: "服務的指導方針隔離 Shell 應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio Shell integrated mode, serviceability
- Shell integrated mode [Visual Studio], serviceability
ms.assetid: 747d1a47-b8b3-4e8b-93c0-768724be48f2
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f4139512bc63141c24b42d0ef3bd53119f4d1fb0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="servicing-guidelines-for-isolated-shell-applications"></a>Isolated 的 Shell 應用程式的服務指導方針
當您發佈的 Visual Studio isolated shell 應用程式時，您必須能夠在安裝之後，您的應用程式提供軟體更新。 若要這樣做，您必須使用 Microsoft Installer (MSI) 檔案安裝應用程式。 這種安裝可讓 web 轉散發 Microsoft 所提供的軟體更新下載，且由您的客戶不需要自訂的介入。  
  
## <a name="servicing-requirements"></a>服務的需求  
 您可以確保獨立的 shell 安裝，可以藉由確定符合下列三個準則，您的安裝程式允許更新。  
  
### <a name="redistribute-by-using-an-msi"></a>轉散發使用 MSI  
 您必須使用 MSI 重新發佈您的應用程式，因為 MSI 會保留產品身分識別，並可確保應用程式的用戶端電腦上的實體位置。 合併模組 （.msm 檔案） 不提供這類保證，而且不應使用。  
  
### <a name="accounting-for-custom-actions"></a>自訂動作的考量  
 自訂動作是在安裝程式中的非標準的安裝指示詞。 自訂動作變更參數，例如檔案位置、 登錄設定、 使用者設定或其他安裝項目。 自訂動作可能會在安裝期間操作資料。  
  
 當您在安裝程式中使用自訂動作時，您必須確定每個安裝階段的自訂動作必須有對應的自訂動作，以復原的動作，當使用者解除安裝應用程式。 如果提供對應程式安裝程式無法解除安裝自訂動作，移除您的應用程式將會保留已部分安裝。  
  
-   當軟體更新會變更這些版本，或者雜湊值，依賴特定版本的檔案或雜湊值的自訂動作將會失敗。 在此情況下您的自訂動作，必須手動更新這些值。 如果產品版本之間共用的檔案或雜湊值的版本，就會發生其他問題。 避免盡可能，此相依性。  
  
### <a name="accounting-for-shared-files"></a>共用檔案的考量  
 共用的檔案有相同名稱，並由多個產品安裝到相同位置。 可能不同版本、 存貨保持單元 (SKU)，或兩者，這些產品和產品可以共存於指定的電腦上。 不過，共用的檔案會建立服務的問題有幾個原因：  
  
-   更新共用的檔案可能會導致應用程式相容性問題，因為一個應用程式的更新可能會變更檔案尚未更新的第二個應用程式所使用的版本。 安裝程式共用檔案的產品計數共用檔案的參考。 因此，解除安裝的產品不會影響超出遞減已安裝的執行個體計數的共用的檔案。  
  
-   快速檢修 (QFE) 安裝程式會還原檔案的 QFE 安裝程式服務的產品版本的版本。 此程序可能會中斷應用程式傳送更新的共用的檔案。