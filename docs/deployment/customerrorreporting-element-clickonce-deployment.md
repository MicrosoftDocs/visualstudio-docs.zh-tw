---
title: '&lt;customErrorReporting&gt;項目 （ClickOnce 部署） |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <customErrorReporting> element [ClickOnce deployment manifest]
ms.assetid: 7d31816e-c692-46b5-9cc9-753284b3bcda
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7254f5735be3efa45b7ba3be0541996cb6c2cc69
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54997633"
---
# <a name="ltcustomerrorreportinggt-element-clickonce-deployment"></a>&lt;customErrorReporting&gt;項目 （ClickOnce 部署）
指定要在錯誤發生時顯示的 URI。  
  
## <a name="syntax"></a>語法  
  
```xml  
<customErrorReporting  
   uri  
/>  
```  
  
## <a name="remarks"></a>備註  
 這是選擇性的項目。 否則，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]會顯示錯誤對話方塊顯示的例外狀況堆疊。 如果`customErrorReporting`項目，則[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]改為將會顯示所指定的 URI`uri`參數。 目標 URI 會包含外部例外狀況類別、 內部例外狀況類別，以及內部例外狀況訊息，做為參數。  
  
 您可以使用此項目新增至您的應用程式報告功能的錯誤。 因為產生的 URI 包含錯誤的類型的相關資訊，該資訊，並顯示，例如，適當的疑難排解畫面內可剖析您的網站。  
  
## <a name="example"></a>範例  
 下列程式碼片段顯示`customErrorReporting`項目，以及它可能會產生所產生的 URI。  
  
```xml
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />  
  
Example Generated Error:  
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.  
```  
  
## <a name="see-also"></a>另請參閱  
 [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)