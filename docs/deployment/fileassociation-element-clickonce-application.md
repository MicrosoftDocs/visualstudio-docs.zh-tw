---
title: '&lt;&gt;ClickOnce 應用程式)  (fileassociation extension 元素 |Microsoft Docs'
description: Fileassociation extension 元素會識別要與應用程式相關聯的副檔名。 Fileassociation extension 元素是選擇性的。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <fileAssociation> element [ClickOnce application manifest]
- manifests [ClickOnce], fileAssociation element
ms.assetid: 8f951b4f-54f9-412e-a9e5-af4e379fcf08
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7435a4e4973ee0a000555e9508328a76f7aa59a6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889144"
---
# <a name="ltfileassociationgt-element-clickonce-application"></a>&lt;&gt;ClickOnce 應用程式)  (fileassociation extension 元素
識別要與應用程式相關聯的副檔名。

## <a name="syntax"></a>Syntax

```xml
<fileAssociation
    xmlns="urn:schemas-microsoft-com:clickonce.v1"
    extension
    description
    progid
    defaultIcon
/>
```

## <a name="elements-and-attributes"></a>元素和屬性
 `fileAssociation` 則是選擇性元素。 元素具有下列屬性。

|屬性|描述|
|---------------|-----------------|
|`extension`|必要。 要與應用程式相關聯的副檔名。|
|`description`|必要。 Shell 所使用之檔案類型的描述。|
|`progid`|必要。 唯一識別檔案類型的名稱。|
|`defaultIcon`|必要。 指定要用於具有此副檔名之檔案的圖示。 您必須使用包含此專案之專案[ \<assembly> 內的](../deployment/assembly-element-clickonce-application.md) [ \<file> 元素](../deployment/file-element-clickonce-application.md)來指定圖示檔。|

## <a name="remarks"></a>備註
 此元素必須包含 "urn：架構-microsoft-com： clickonce. v1" 的 XML 命名空間參考。 如果 `<fileAssociation>` 使用專案，它必須 `<application>` 在其父[ \<assembly> 元素](../deployment/assembly-element-clickonce-application.md)中的元素之後。

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 將不會覆寫現有的檔案關聯。 不過，ClickOnce 應用程式只能覆寫目前使用者的副檔名。 在該 ClickOnce 應用程式卸載之後，ClickOnce 會刪除該使用者的檔案關聯，而每部機器的關聯也會再次處於作用中狀態。

## <a name="example"></a>範例
 下列程式碼範例說明 `fileAssociation` 使用所部署的文字編輯器應用程式之應用程式資訊清單中的元素 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。 這個程式碼範例也包含屬性所需的[ \<file> 元素](../deployment/file-element-clickonce-application.md) `defaultIcon` 。

```xml
<file name="text.ico" size="4286">
  <hash>
    <dsig:Transforms>
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
    </dsig:Transforms>
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
    <dsig:DigestValue>0joAqhmfeBb93ZneZv/oTMP2brY=</dsig:DigestValue>
  </hash>
</file>
<file name="writing.ico" size="9662">
  <hash>
    <dsig:Transforms>
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
    </dsig:Transforms>
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
    <dsig:DigestValue>2cL2U7cm13nG40v9MQdxYKazIwI=</dsig:DigestValue>
  </hash>
</file>
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".text" description="Text  Document (ClickOnce)" progid="Text.Document" defaultIcon="text.ico" />
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".writing" description="Writings (ClickOnce)" progid="Writing.Document" defaultIcon="writing.ico" />
```

## <a name="see-also"></a>另請參閱
- [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)