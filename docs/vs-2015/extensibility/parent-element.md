---
title: 父項目 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b16aa3e3d6542130b449196de92e795e464ab0e9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47490499"
---
# <a name="parent-element"></a>Parent 項目
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[父元素](https://docs.microsoft.com/visualstudio/extensibility/parent-element)。  
  
按鈕或下拉式方塊的父代可能只是群組。 功能表或群組的父系可能是功能表或群組。 在  [CommandPlacement 元素](../extensibility/commandplacement-element.md)，則需要這個元素; 所有其他執行個體中是選擇性的。 如果省略這個項目，則父代`Group_Undefined:0`會隱含。  
  
## <a name="syntax"></a>語法  
  
```  
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|guid|必要。 GUID/識別碼 GUID 命令識別項。|  
|id|必要。 識別碼的 GUID/識別碼命令識別項。|  
  
### <a name="child-elements"></a>子元素  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[CommandTable 元素](../extensibility/commandtable-element.md)|定義代表命令的 VSPackage 提供整合式的開發環境 (IDE) 的所有項目。 例如，功能表項目、 功能表、 工具列和下拉式方塊。|  
|[Buttons 元素](../extensibility/buttons-element.md)|群組[Button Element](../extensibility/button-element.md)項目。|  
|[Menus 元素](../extensibility/menus-element.md)|定義實作 VSPackage 的所有功能表。|  
|[Groups 元素](../extensibility/groups-element.md)|包含定義 VSPackage 的命令群組的項目。|  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

