---
title: ClickOnce 快取總覽 |Microsoft Docs
description: 瞭解 ClickOnce 應用程式快取，此快取包含儲存 ClickOnce 應用程式之用戶端電腦上的隱藏目錄。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 12c14850717688b17caed2fbe7feb546e0ebdb6e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936167"
---
# <a name="clickonce-cache-overview"></a>ClickOnce 快取概觀
所有 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式（不論是在本機安裝或裝載于線上）都會儲存在用戶端電腦上的應用程式快取中 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。  快取 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 是在目前使用者的 [檔和設定] 資料夾的本機設定目錄下的隱藏目錄系列。 此快取會保存應用程式的所有檔案，包括元件、設定檔、應用程式和使用者設定，以及資料目錄。 快取也負責將應用程式的資料目錄遷移至最新版本。 如需資料移轉的詳細資訊，請參閱 [在 ClickOnce 應用程式中存取本機和遠端資料](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)。

 藉由提供單一位置來儲存應用程式， [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 可將管理應用程式實體安裝的工作從使用者接管。 快取也會將所有應用程式的元件和資料檔和彼此分開的不同版本保持在一起，有助於隔離應用程式。 例如，當您升級 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式時，該版本和其資料資源會在快取中提供自己的目錄。

## <a name="cache-storage-quota"></a>快取儲存體配額
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 在線上裝載的應用程式會受到限制快取大小的配額所能佔用的空間數量限制 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。 快取大小會套用至所有使用者的線上應用程式;單一的部分信任線上應用程式僅限於佔用一半的配額空間。 已安裝的應用程式不會受到快取大小的限制，而且不會計入快取限制。 對於所有 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式，快取只會保留目前的版本和先前安裝的版本。

 用戶端電腦預設會有 250 MB 的儲存空間供線上 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式使用。 資料檔案不計入此限制。 系統管理員可以藉由變更登錄機碼 **HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment\OnlineAppQuotaInKB** 來放大或減少特定用戶端電腦上的此配額，這是表示快取大小（以 kb 為單位）的 DWORD 值。 例如，為了將快取大小縮減為 50 MB，您可以將此值變更為51200。

## <a name="see-also"></a>另請參閱
- [在 ClickOnce 應用程式中存取本機和遠端資料](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)