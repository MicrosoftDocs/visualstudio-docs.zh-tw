---
title: ClickOnce 快取總覽 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce deployemtn
- ClickOnce applications, cache
- ClickOnce deployment, cache
ms.assetid: e379921e-9ef1-4326-bbf3-53ba67925526
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3d7abeeec4a640119e3089c795ac529a10f8dc09
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2020
ms.locfileid: "84182621"
---
# <a name="clickonce-cache-overview"></a>ClickOnce 快取概觀
所有 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式（不論是安裝在本機或裝載于線上）都會儲存在用戶端電腦 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 的*cache*應用程式快取中。 快取 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 是目前使用者的 [檔和設定] 資料夾之 [本機設定] 目錄底下的隱藏目錄系列。 此快取會保存所有應用程式的檔案，包括元件、設定檔、應用程式和使用者設定，以及資料目錄。 快取也會負責將應用程式的資料目錄遷移至最新版本。 如需資料移轉的詳細資訊，請參閱[在 ClickOnce 應用程式中存取本機和遠端資料](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)。

 藉由提供應用程式儲存區的單一位置， [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 會接管從使用者管理應用程式實體安裝的工作。 快取也會將所有應用程式及其不同版本之間的元件和資料檔案分開，以協助隔離應用程式。 例如，當您升級 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式時，該版本和其資料資源會在快取中提供自己的目錄。

## <a name="cache-storage-quota"></a>快取儲存體配額
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]在線上裝載的應用程式會受限於配額限制快取大小所能佔用的空間量 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。 快取大小會套用至所有使用者的線上應用程式;單一部分信任的線上應用程式僅限於佔用一半的配額空間。 已安裝的應用程式不會受到快取大小的限制，而且不會計算快取限制。 對於所有 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式，快取只會保留目前版本和先前安裝的版本。

 根據預設，用戶端電腦的線上應用程式會有 250 MB 的儲存空間 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。 資料檔案未計入此限制。 系統管理員可以藉由變更登錄機碼（ **HKEY_CURRENT_USER \software\classes\software\microsoft\windows\currentversion\deployment\onlineappquotainkb**，這是表示快取大小（以 kb 為單位）的 DWORD 值，來放大或減少特定用戶端電腦上的此配額。 例如，為了將快取大小縮減為 50 MB，您會將此值變更為51200。

## <a name="see-also"></a>另請參閱
- [在 ClickOnce 應用程式中存取本機和遠端資料](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)