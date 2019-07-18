---
title: '&lt;增益集&gt;元素 （在 Visual Studio 中的 Office 程式開發）'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <addIn> element
- addin element
- <addin> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3ab7b0617f09b98c9e30c7f198ef0e2aaa301e33
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62931002"
---
# <a name="ltaddingt-element-office-development-in-visual-studio"></a>&lt;增益集&gt;元素 （在 Visual Studio 中的 Office 程式開發）
  **Addin**項目`vstav3`命名空間包含的是 Microsoft Office VSTO 增益集和使用 Visual Studio 開發的文件層級自訂專屬的資訊。

## <a name="syntax"></a>語法

```xml
<addIn>
  <entryPointsCollection>
    <entryPoints>
      <entryPoint>
      </entryPoint>
    </entryPoints>
  </entryPointsCollection>
  <update></update>
  <postActions>
    <postAction>
      <postActionData>
      </postActionData>
    <postAction>
  </postActions>
  <application>
    <customization>
    </customization>
  </application
</addIn>
```

## <a name="elements-and-attributes"></a>元素和屬性
 **Addin**項目`vstav3`命名空間包含 Office 方案和 Microsoft Office 應用程式的相關資訊。 此項目必須位於下列命名空間中： `vstav3=urn:schemas-microsoft-com:vsta.v3`。 子項目也必須在這個命名空間中。

 `addin` 項目沒有任何屬性。

 `addin` 項目具有下列子項目。

### <a name="entrypoints"></a>entryPoints
 必要項。 **進入點**項目所述[&#60;進入點&#62;項目的&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md)。

### <a name="update"></a>更新
 必要項。 **更新**項目所述[&#60;更新&#62;項目的&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/update-element-office-development-in-visual-studio.md)。

### <a name="postactions"></a>postActions
 選擇性。 **PostActions**項目所述[ &#60;postActions&#62;項目的&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/postactions-element-office-development-in-visual-studio.md)。

### <a name="application"></a>應用程式
 必要項。 **應用程式**項目所述[&#60;應用程式&#62;項目的&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/application-element-office-development-in-visual-studio.md)。

## <a name="document-level-customization-example"></a>文件層級自訂範例

### <a name="description"></a>描述
 下列程式碼範例說明**addin**您可以使用部署之文件層級 Office 方案中的項目[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]。 此程式碼範例是中提供之較大範例的一部分[Application manifests for Office 方案](../vsto/application-manifests-for-office-solutions.md)。

### <a name="code"></a>程式碼

```xml
<vstav3:addIn
  xmlns:vstav3="urn:schemas-microsoft-com:vsta.v3">
  <vstav3:entryPointsCollection>
    <vstav3:entryPoints>
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
    </vstav3:entryPoints>
  </vstav3:entryPointsCollection>
  <vstav3:update
    enabled="true">
    <vstav3:expiration
      maximumAge="7"
      unit="days" />
  </vstav3:update>
  <vstav3:application>
    <vstov4:customizations
      xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">
      <vstov4:customization>
        <vstov4:document
          solutionId="73e" />
      </vstov4:customization>
    </vstov4:customizations>
  </vstav3:application>
</vstav3:addIn>
```

## <a name="vsto-add-in-example"></a>VSTO 增益集範例

### <a name="description"></a>描述
 下列程式碼範例說明**addin**您可以使用部署應用程式層級 Office 方案中的項目[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]。 此程式碼範例是中提供之較大範例的一部分[Application manifests for Office 方案](../vsto/application-manifests-for-office-solutions.md)。

### <a name="code"></a>程式碼

```xml
<vstav3:addIn
  xmlns:vstav3="urn:schemas-microsoft-com:vsta.v3">
  <vstav3:entryPointsCollection>
    <vstav3:entryPoints>
      <vstav3:entryPoint
        class="ContosoOutlookAddIn.ThisAddIn">
        <assemblyIdentity
          name="ContosoOutlookAddIn"
          version="1.0.0.0"
          language="neutral"
          processorArchitecture="msil" />
      </vstav3:entryPoint>
    </vstav3:entryPoints>
  </vstav3:entryPointsCollection>
  <vstav3:update
    enabled="true">
    <vstav3:expiration
      maximumAge="7"
      unit="days" />
  </vstav3:update>
  <vstav3:application>
    <vstov4:customizations
      xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">
      <vstov4:customization>
        <vstov4:appAddIn
          application="Outlook"
          loadBehavior="3"
          keyName="ContosoOutlookAddIn">
          <vstov4:friendlyName>
            ContosoOutlookAddIn
          </vstov4:friendlyName>
          <vstov4:description>
            ContosoOutlookAddIn - Outlook VSTO Add-in
            created with Visual Studio Tools for Office
          </vstov4:description>
          <vstov4:formRegions>
            <vstov4:formRegion
                name="OutlookAddIn1.FormRegion1">
              <vstov4:messageClass name="IPM.Note" />
              <vstov4:messageClass name="IPM.Contact" />
              <vstov4:messageClass name="IPM.Appointment" />
            </vstov4:formRegion>
          </vstov4:formRegions>
        </vstov4:appAddIn>
      </vstov4:customization>
    </vstov4:customizations>
  </vstav3:application>
</vstav3:addIn>
```

## <a name="see-also"></a>另請參閱

- [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)
- [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)