---
title: HOW TO：ClickOnce 應用程式設定的安全性區域 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, security settings
- code access security, ClickOnce applications
- security zones, ClickOnce applications
ms.assetid: d3dac454-518a-44d7-a76e-ccb7b9c3a150
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 31a61dd337fce614c1271f994a42ec90f3be8acb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62898385"
---
# <a name="how-to-set-a-security-zone-for-a-clickonce-application"></a>HOW TO：為 ClickOnce 應用程式設定安全性區域
設定 ClickOnce 應用程式的程式碼存取安全性權限時，必須從 [專案設計工具]  之 [安全性] 頁面上的一組基底權限開始。

 在大多數情況下，您也可以選擇 [網際網路]  區域 (包含一組有限的權限) 或 [近端內部網路]  區域 (包含一組更高的權限)。 如果應用程式需要自訂權限，您可以選擇 [自訂]  安全性區域來完成。 如需有關設定自訂權限的詳細資訊，請參閱[How to:設定 ClickOnce 應用程式的自訂權限](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)。

### <a name="to-set-a-security-zone"></a>設定安全性區域

1. 選取方案總管 中的專案，然後按一下 [專案]  功能表中的 [屬性] 。

2. 按一下 [ **安全性** ] 索引標籤。

3. 選取 [啟用 ClickOnce 安全性設定]  核取方塊。

4. 選取 [這是部分信任的應用程式]  選項按鈕。

     這會啟用 [ClickOnce 安全性權限]  區段中的控制項。

5. 在 [安裝應用程式的區域]  下拉式清單中，選取安全性區域。

## <a name="see-also"></a>另請參閱
- [如何：設定 ClickOnce 應用程式的自訂權限](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)
- [ClickOnce 應用程式的程式碼存取安全性](../deployment/code-access-security-for-clickonce-applications.md)
