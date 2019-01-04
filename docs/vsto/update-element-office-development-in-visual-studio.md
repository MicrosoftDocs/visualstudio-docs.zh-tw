---
title: '&lt;更新&gt;元素 （在 Visual Studio 中的 Office 程式開發）'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- update element
- <update> element
- application manifests [Office development in Visual Studio], <update> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 661aa9c0c1a590e78d20e52b6321294d59e70c63
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53988984"
---
# <a name="ltupdategt-element-office-development-in-visual-studio"></a>&lt;更新&gt;元素 （在 Visual Studio 中的 Office 程式開發）
  `update`項目指定的方案將會檢查更新的間隔。

## <a name="syntax"></a>語法

```xml
<update
  enabled>
  <expiration
    maximumAge
    unit
  />
</update>
```

## <a name="elements-and-attributes"></a>項目和屬性
 `update` 項目是必要的，且位於 `vstav3` 命名空間。

 `update` 項目具有下列屬性。

|屬性|描述|
|---------------|-----------------|
|`enabled`|必要項。 將 enabled 設定為下列值之一：<br /><br /> -   **true**檢查更新。<br />-   **false**以防止 檢查更新。|

 `update` 項目具有下列子項目。

### <a name="expiration"></a>到期日
 `expiration` 項目是必要的，且位於 `vstav3` 命名空間。 這個元素指定的方案檢查更新的間隔。

 `expiration` 項目具有下列屬性。

|屬性|描述|
|---------------|-----------------|
|`maximumAge`| 必要項。 將此選項設定為整數。|
|`unit`|必要項。 設定`unit`下列值之一：<br /><br /> -   **時數**<br />-   **天**<br />-   **週**|

## <a name="example-of-always-checking-for-updates"></a>一律檢查更新的範例

### <a name="description"></a>描述
 下列程式碼範例說明`update`設在 Office 方案中的更新一定要檢查的項目。

### <a name="code"></a>程式碼

```xml
<vstav3:update enabled="true" />
```

## <a name="example-of-setting-a-default-update-interval"></a>設定預設的更新間隔的範例

### <a name="description"></a>描述
 下列程式碼範例說明`update`Office 方案的應用程式資訊清單中的項目。 此程式碼範例是中提供之較大範例的一部分[Application manifests for Office 方案](../vsto/application-manifests-for-office-solutions.md)。

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
