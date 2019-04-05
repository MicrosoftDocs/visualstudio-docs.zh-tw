---
title: 部署 ClickOnce 應用程式進行測試和實際執行伺服器，但不重新簽署 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, deploying without resigning
- ClickOnce deployment, without resigning
- application updates, ClickOnce
- update location [ClickOnce]
- deploymentProvider tag
- manifests [ClickOnce]
ms.assetid: 1218a98d-1ad5-4eef-95dd-0e0b3c44168c
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2354f65e1b042682a0e58a0dbb4bc12712bb47e3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58939593"
---
# <a name="deploying-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>針對測試和實際執行伺服器部署 ClickOnce 應用程式但不重新簽章
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題討論 ClickOnce 導入.NET Framework 3.5 版可讓部署 ClickOnce 應用程式，從多個網路位置，而不重新簽署，或變更 ClickOnce 資訊清單中的新功能。  
  
> [!NOTE]
>  重新簽署，仍然是部署新版本的應用程式的慣用的方法。 可能的話，使用重新簽章的方法。 如需詳細資訊，請參閱 [Mage.exe (資訊清單產生和編輯工具)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)。  
  
 第三方開發人員和 Isv 可以選擇加入，以在這項功能，讓他們的客戶更新其應用程式更容易。 這項功能可以用於下列情況：  
  
-   當正在更新應用程式時，不應用程式第一次安裝。  
  
-   只能在一個設定的電腦上的應用程式時。 例如，如果應用程式設定為指向兩個不同的資料庫，您無法使用這項功能。  
  
## <a name="excluding-deploymentprovider-from-deployment-manifests"></a>部署資訊清單時，排除 deploymentProvider  
 在.NET Framework 2.0 和.NET Framework 3.0 中，會在離線可用性的系統安裝任何 ClickOnce 應用程式必須指定`deploymentProvider`部署資訊清單中。 `deploymentProvider`通常稱為更新位置; 它是應用程式更新會檢查 ClickOnce 的位置。 這項需求，再加上需要讓應用程式發行者登入他們的部署，並不容易更新 ClickOnce 應用程式從廠商或其他第三方公司。 它也使它更難以部署相同的應用程式，從相同網路上的多個位置。  
  
 使用 clickonce，.NET Framework 3.5 中所做的變更，它可能會提供 ClickOnce 應用程式，然後將它自己的網路上的應用程式部署中的另一個組織的第三方。  
  
 若要利用這項功能，ClickOnce 應用程式開發人員必須排除`deploymentProvider`從其部署資訊清單。 這表示不含`-providerUrl`引數，當您建立部署資訊清單使用 Mage.exe，或是確保**啟動的位置**文字方塊中**應用程式資訊清單** 索引標籤會保留空白如果您會產生使用 MageUI.exe 部署資訊清單。  
  
## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider 和應用程式更新  
 從.NET Framework 3.5 開始，您不再需要指定`deploymentProvider`在您的部署資訊清單，若要部署 ClickOnce 應用程式的線上和離線的使用方式。 這可支援您要封裝和簽署部署，但是可讓他們的網路上部署應用程式的其他公司的案例。  
  
 要記住的重點是，排除的應用程式`deploymentProvider`無法在更新期間變更其安裝位置，直到它們寄送包含的更新`deploymentProvider`標記一次。  
  
 以下是兩個範例說明此點。 在第一個範例中，您可以發行 ClickOnce 應用程式沒有任何`deploymentProvider`標記，而且您要求使用者安裝從 http://www.adatum.com/MyApplication/ 。 如果您決定您想要將應用程式的下一個更新發行 http://subdomain.adatum.com/MyApplication/，您會有沒有辦法這表示部署資訊清單位於 http://www.adatum.com/MyApplication/。 您可以執行下列其中一種：  
  
- 告知使用者解除安裝舊的版本，並從新位置中安裝新的版本。  
  
- 在 包含更新 http://www.adatum.com/MyApplication/ ，其中包含`deploymentProvider`指向 http://www.adatum.com/MyApplication/。 然後，發行與更新版本的另一個更新`deploymentProvider`指向 http://subdomain.adatum.com/MyApplication/ 。  
  
  在第二個範例中，您可以發行 ClickOnce 應用程式，指定`deploymentProvider`，但後來將它移除。 一次新的版本不含`deploymentProvider`已下載至用戶端，您將無法用於更新，直到您發行的版本，具有應用程式的路徑重新導向`deploymentProvider`還原。 如同第一個範例中，`deploymentProvider`一開始必須指向目前的更新位置，不是您新的位置。 在此情況下，如果您嘗試插入`deploymentProvider`，這是指 http://subdomain.adatum.com/MyApplication/，則下一次的更新會失敗。  
  
## <a name="creating-a-deployment"></a>建立部署  
 如需建立可以從不同的網路位置進行部署的部署的逐步指引，請參閱[逐步解說：手動部署 ClickOnce 應用程式不需要重新簽署而且會保留商標資訊](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required?view=vs-2015)。  
  
## <a name="see-also"></a>另請參閱  
 [Mage.exe (資訊清單產生和編輯工具)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [MageUI.exe (資訊清單產生和編輯工具、圖形用戶端)](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)
