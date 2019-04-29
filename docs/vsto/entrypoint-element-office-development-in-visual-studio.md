---
title: '&lt;entryPoint&gt;元素 （在 Visual Studio 中的 Office 程式開發）'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <entryPoint> element
- <entryPoint> element
- entryPoint element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bd3da83a25a05690e56d229f61ee709473171dd7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62799782"
---
# <a name="ltentrypointgt-element-office-development-in-visual-studio"></a>&lt;entryPoint&gt;元素 （在 Visual Studio 中的 Office 程式開發）
  每個 `entryPoint` 命名空間的 `vstav3` 項目都會識別出安裝這個 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 應用程式時應該執行的自訂組件。

## <a name="syntax"></a>語法

```xml
<entryPoint class>
    <assemblyIdentity />
</entryPoint>
```

## <a name="elements-and-attributes"></a>元素和屬性
 `entryPoint` 項目是必要的，且位於 `vstav3` 命名空間。

 每個 `entryPoint` 項目只可以包含一個自訂組件。 在應用程式資訊清單中可以定義多個 `entryPoint` 項目。

 `entryPoint` 項目具有下列屬性。

|屬性|描述|
|---------------|-----------------|
|`class`|必要項。 識別要執行的自訂組件。 這個屬性的語法是 *NamespaceName.ClassName*。|

 `entryPoint` 具有下列項目。

### <a name="assemblyidentity"></a>assemblyIdentity
 必要項。 `assemblyIdentity` 命名空間中的 `vstav3` 項目參考 `assemblyIdentity` 應用程式資訊清單中的現有 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 項目。

 所扮演的角色`assemblyIdentity`和其屬性定義於[&#60;組件識別&#62;項目&#40;ClickOnce 應用程式&#41;](../deployment/assemblyidentity-element-clickonce-application.md)。

## <a name="document-level-customization-example"></a>文件層級自訂範例

### <a name="description"></a>描述
 下列程式碼範例說明使用 `entryPoint` 所部署之文件層級 Office 解決方案應用程式資訊清單中的 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]項目。 此程式碼範例是中提供之較大範例的一部分[Application manifests for Office 方案](../vsto/application-manifests-for-office-solutions.md)。

### <a name="code"></a>程式碼

```xml
<vstav3:entryPoint
  class="ContosoExcelWorkbook.ThisWorkbook">
  <assemblyIdentity
    name="ContosoExcelWorkbook"
    version="1.0.0.0"
    language="neutral"
    processorArchitecture="msil" />
</vstav3:entryPoint>
<vstav3:entryPoint
  class="ContosoExcelWorkbook.Sheet1">
  <assemblyIdentity
    name="ContosoExcelWorkbook"
    version="1.0.0.0"
    language="neutral"
    processorArchitecture="msil" />
</vstav3:entryPoint>
<vstav3:entryPoint
  class="ContosoExcelWorkbook.Sheet2">
  <assemblyIdentity
    name="ContosoExcelWorkbook"
    version="1.0.0.0"
    language="neutral"
    processorArchitecture="msil" />
</vstav3:entryPoint>
<vstav3:entryPoint
  class="ContosoExcelWorkbook.Sheet3">
  <assemblyIdentity
    name="ContosoExcelWorkbook"
    version="1.0.0.0"
    language="neutral"
    processorArchitecture="msil" />
</vstav3:entryPoint>
```

## <a name="vsto-add-in-example"></a>VSTO 增益集範例

### <a name="description"></a>描述
 下列程式碼範例說明使用 `entryPoint` 所部署之應用程式層級 Office 解決方案應用程式資訊清單中的 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]項目。 此程式碼範例是中提供之較大範例的一部分[Application manifests for Office 方案](../vsto/application-manifests-for-office-solutions.md)。

### <a name="code"></a>程式碼

```xml
<vstav3:entryPoint
  class="ContosoOutlookAddIn.ThisAddIn">
  <assemblyIdentity
    name="ContosoOutlookAddIn"
    version="1.0.0.0"
    language="neutral"
    processorArchitecture="msil" />
</vstav3:entryPoint>
```

## <a name="see-also"></a>另請參閱

- [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)
- [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)