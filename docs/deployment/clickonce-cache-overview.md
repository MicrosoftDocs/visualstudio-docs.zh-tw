---
title: "ClickOnce 快取概觀 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
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
caps.latest.revision: "12"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 1aa73140760f161971f30e4232658b18453f233f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="clickonce-cache-overview"></a>ClickOnce 快取概觀
所有[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式，無論它們是安裝在本機，或裝載於線上，會儲存在用戶端電腦[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式*快取*。 A[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]快取是一系列的本機設定目錄的目前使用者的 [Documents and Settings] 資料夾底下的隱藏目錄。 此快取保存應用程式的所有檔案，包括組件、 組態檔、 應用程式和使用者設定和資料目錄。 快取也會負責將應用程式的資料目錄移轉到最新版本。 如需有關資料移轉的詳細資訊，請參閱[存取本機和 ClickOnce 應用程式中的遠端資料](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)。  
  
 藉由提供應用程式儲存區中，單一位置[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]高於管理應用程式的實體安裝從使用者的工作。 快取也有助於隔離應用程式會保留組件和資料檔案的所有應用程式封裝，並從另一個將其不同版本。 例如，當您升級[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式中，提供版本和其資料資源，以自己的目錄快取中。  
  
## <a name="cache-storage-quota"></a>快取的儲存配額  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]它們可能會佔據的空間數量會限制大小的配額限制之應用程式裝載於線上[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]快取。 快取大小適用於所有使用者的線上應用程式。一個單一的部分信任的線上應用程式僅限於佔用一半的配額空間。 已安裝應用程式不會受到快取大小，並不會計入快取限制。 所有[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式，快取保留目前的版本和先前安裝的版本。  
  
 根據預設，用戶端電腦有 250 MB 的儲存體的線上[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式。 這項限制不計算的資料檔案。 系統管理員可以放大或縮小特定用戶端電腦上的此配額變更登錄機碼，HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment\OnlineAppQuotaInKB，也就是 DWORD 值表示快取大小，以 kb 為單位。 例如，為了減少快取大小為 50 MB，您會為 51200 變更此值。  
  
## <a name="see-also"></a>另請參閱  
 [在 ClickOnce 應用程式中存取本機和遠端資料](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)