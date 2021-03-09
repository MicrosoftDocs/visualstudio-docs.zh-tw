---
title: '&lt;&gt;Visual Studio) 中 (Office 開發的 update 元素'
description: Update 元素會指定方案檢查更新的間隔。
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- update element
- <update> element
- application manifests [Office development in Visual Studio], <update> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 59e7b21902c486bd78548cd79f2e79a5056042a5
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2021
ms.locfileid: "102468502"
---
# <a name="ltupdategt-element-office-development-in-visual-studio"></a>&lt;&gt;Visual Studio) 中 (Office 開發的 update 元素
  `update`元素會指定方案檢查更新的間隔。

## <a name="syntax"></a>Syntax

```xml
<update
  enabled>
  <expiration
    maximumAge
    unit
  />
</update>
```

## <a name="elements-and-attributes"></a>元素和屬性
 `update` 項目是必要的，且位於 `vstav3` 命名空間。

 `update` 項目具有下列屬性。

|屬性|描述|
|---------------|-----------------|
|`enabled`|必要。 將 [啟用] 設定為下列其中一個值：<br /><br /> -   **true** 表示檢查是否有更新。<br />-   **false** 以防止檢查更新。|

 `update` 項目具有下列子項目。

### <a name="expiration"></a>expiration
 `expiration` 項目是必要的，且位於 `vstav3` 命名空間。 這個元素會指定方案檢查更新的間隔。

 `expiration` 項目具有下列屬性。

|屬性|描述|
|---------------|-----------------|
|`maximumAge`| 必要。 將此設為等於整數。|
|`unit`|必要。 設定 `unit` 為下列其中一個值：<br /><br /> -   **小時**<br />-   **天**<br />-   **星期**|

## <a name="example-of-always-checking-for-updates"></a>一律檢查更新的範例

### <a name="description"></a>描述
 下列程式碼範例將說明 `update` 設定為一律檢查 Office 方案中更新的元素。

### <a name="code"></a>程式碼

```xml
<vstav3:update enabled="true" />
```

## <a name="example-of-setting-a-default-update-interval"></a>設定預設更新間隔的範例

### <a name="description"></a>描述
 下列程式碼範例說明 `update` Office 方案的應用程式資訊清單中的元素。 這個程式碼範例是 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)中所提供之較大範例的一部分。

### <a name="code"></a>程式碼

```xml
<vstav3:update enabled="true">
    <vstav3:expiration maximumAge="7" unit="days" />
</vstav3:update>
```

## <a name="see-also"></a>另請參閱

- [使用 ClickOnce 部署 Office 方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)
- [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)
