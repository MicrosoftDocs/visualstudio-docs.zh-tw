---
title: ClickOnce 快取概觀 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce deployemtn
- ClickOnce applications, cache
- ClickOnce deployment, cache
ms.assetid: e379921e-9ef1-4326-bbf3-53ba67925526
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 5fb0bcd8c589f8ade12f8da0c4151e1f2894dd1d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47485526"
---
# <a name="clickonce-cache-overview"></a>ClickOnce 快取概觀
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[ClickOnce 快取概觀](https://docs.microsoft.com/visualstudio/deployment/clickonce-cache-overview)。  
  
所有[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]應用程式，無論它們是在本機安裝或線上，儲存在用戶端電腦[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]應用程式*快取*。 A[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]快取是一系列的隱藏目前使用者的 Documents and Settings 資料夾的本機設定目錄底下的目錄。 此快取保留應用程式的所有檔案，包括組件、 組態檔、 應用程式和使用者設定和資料目錄。 快取也會負責將應用程式的資料目錄移轉到最新版本的。 如需有關資料移轉的詳細資訊，請參閱[存取本機和 ClickOnce 應用程式中的遠端資料](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)。  
  
 藉由提供單一位置的應用程式存放區，[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]高於管理實體的安裝應用程式的使用者的工作。 快取也有助於隔離應用程式是將保留組件和資料檔案的所有應用程式，其不同的版本與彼此分開。 例如，當您升級[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]應用程式，提供版本和其資料資源，使用自己的快取中的目錄。  
  
## <a name="cache-storage-quota"></a>快取儲存體配額  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 線上裝載的應用程式類型受限於他們可以佔用的空間量限制大小的配額[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]快取。 快取大小適用於所有使用者的線上應用程式;單一的部分信任的線上應用程式僅限於佔用一半的配額空間。 已安裝的應用程式不會受到快取大小，而且不會計入快取限制。 所有[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]應用程式，快取會保留目前的版本與先前安裝的版本。  
  
 根據預設，用戶端電腦有 250 MB 的儲存體的線上[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]應用程式。 資料檔案不會計入這項限制。 系統管理員可以放大或縮小這個配額的特定用戶端電腦上變更登錄機碼，而 HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment\OnlineAppQuotaInKB，也就是 DWORD 值表示快取大小 （kb）。 比方說，為了減少快取大小為 50 MB，您會為 51200 變更此值。  
  
## <a name="see-also"></a>另請參閱  
 [在 ClickOnce 應用程式中存取本機和遠端資料](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)



