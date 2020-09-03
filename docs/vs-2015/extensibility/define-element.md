---
title: Define 元素 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Define
- Define element (VSCT XML schema)
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8cc543a07176f307641c53a2ef3e132881821ce7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162162"
---
# <a name="define-element"></a>Define 項目
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

定義符號名稱和值組。 條件式屬性可以評估此符號。 如需詳細資訊，請參閱 [條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。 另請參閱 [符號元素](../extensibility/symbols-element.md)。  
  
## <a name="syntax"></a>語法  
  
```  
<Define name="Mode" value="Standard" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|NAME|必要。 符號的名稱：<br /><br /> name = "Mode"|  
|value|必要。 符號的值：<br /><br /> 值 = "Standard"|  
|條件|選擇性。 如需詳細資訊，請參閱 [條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[CommandTable 元素](../extensibility/commandtable-element.md)|定義代表 VSPackage 提供給整合式開發環境 (IDE) 命令的所有元素。 例如，功能表項目、功能表、工具列和下拉式方塊。|  
  
## <a name="example"></a>範例  
  
```  
<Define name="DEMO_UI"/>  
<Define name="MODE" value="Standard"/>  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
