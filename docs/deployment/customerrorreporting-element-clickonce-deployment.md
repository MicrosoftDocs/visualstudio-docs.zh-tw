---
title: '&lt;customErrorReporting&gt;元素 （ClickOnce 部署） |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 41ade854a37127443735e1c197c080aad3d5bd93
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="ltcustomerrorreportinggt-element-clickonce-deployment"></a>&lt;customErrorReporting&gt;元素 （ClickOnce 部署）
指定要在錯誤發生時顯示的 URI。  
  
## <a name="syntax"></a>語法  
  
```  
<customErrorReporting  
   uri  
/>  
```  
  
## <a name="remarks"></a>備註  
 這是選擇性的項目。 未安裝，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]會顯示錯誤對話方塊顯示例外狀況堆疊。 如果`customErrorReporting`項目不存在，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]改為將會顯示所指定的 URI`uri`參數。 目標 URI 包含外部例外狀況類別、 內部例外狀況類別，以及內部例外狀況訊息做為參數。  
  
 使用此項目加入至您的應用程式報告功能的錯誤。 所產生的 URI 包含有關錯誤的類型，因為該資訊，並顯示，例如，適當的疑難排解畫面，可以剖析您的網站。  
  
## <a name="example"></a>範例  
 下列程式碼片段說明`customErrorReporting`項目，以及它可能會產生所產生的 URI。  
  
```  
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />  
  
Example Generated Error:  
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.  
```  
  
## <a name="see-also"></a>另請參閱  
 [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)