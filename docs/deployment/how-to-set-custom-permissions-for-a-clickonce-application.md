---
title: HOW TO：設定 ClickOnce 應用程式的自訂權限 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, permissions
- permissions, ClickOnce applications
ms.assetid: 660459ca-ef73-44a8-b323-610001f63b93
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d275875b18941df63e0f6ee3c17f427334eab88a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60058540"
---
# <a name="how-to-set-custom-permissions-for-a-clickonce-application"></a>HOW TO：為 ClickOnce 應用程式設定自訂權限
您可以部署對網際網路或近端內部網路區域使用預設權限的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式。 或者，您可以建立應用程式所需特定權限的自訂區域。 做法是在 [專案設計工具]  的 [安全性] 頁面上自訂安全性權限。

### <a name="to-customize-a-permission"></a>自訂權限

1. 在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。

2. 按一下 [ **安全性** ] 索引標籤。

3. 選取 [啟用 ClickOnce 安全性設定]  核取方塊。

4. 選取 [這是部分信任的應用程式]  選項按鈕。

     這會啟用 [ClickOnce 安全性權限]  區段中的控制項。

5. 從 [安裝應用程式的區域]  下拉式清單中，按一下 [(自訂)] 。

6. 按一下 [編輯權限 XML] 。

     即會在 [XML 編輯器] 中開啟 *app.manifest* 檔案。

7. 在 `</applicationRequestMinimum>` 項目之前，新增應用程式所需權限的 XML 程式碼。

    > [!NOTE]
    >  您可以使用權限集的 `ToXml` 方法，產生應用程式資訊清單的 XML 程式碼。 例如，若要產生 <xref:System.Security.Permissions.EnvironmentPermission> 權限集的 XML，請呼叫 <xref:System.Security.Permissions.EnvironmentPermission.ToXml%2A> 方法。

## <a name="see-also"></a>另請參閱
- [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)
- [ClickOnce 應用程式的程式碼存取安全性](../deployment/code-access-security-for-clickonce-applications.md)
