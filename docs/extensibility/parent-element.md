---
title: "父項目 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fc66e193b13ac6baf9d6089483a1281c2d6a59ef
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="parent-element"></a>Parent 項目
按鈕或下拉式方塊的父代可能只是群組。 功能表或群組的父系可能是功能表或群組。 在[CommandPlacement 元素](../extensibility/commandplacement-element.md)，則需要這個元素; 所有其他執行個體中是選擇性的。 如果省略這個項目，則父代`Group_Undefined:0`會隱含。  
  
## <a name="syntax"></a>語法  
  
```  
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|說明|  
|---------------|-----------------|  
|Guid|必要項。 GUID/識別碼 GUID 命令識別項。|  
|id|必要項。 識別碼的 GUID/識別碼命令識別項。|  
  
### <a name="child-elements"></a>子元素  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[CommandTable 元素](../extensibility/commandtable-element.md)|定義代表 VSPackage 提供的命令到整合式的開發環境 (IDE) 的所有項目。 例如，功能表項目、 功能表、 工具列和下拉式方塊。|  
|[Buttons 元素](../extensibility/buttons-element.md)|群組[按鈕項目](../extensibility/button-element.md)項目。|  
|[Menus 元素](../extensibility/menus-element.md)|定義所有實作 VSPackage 的功能表。|  
|[Groups 元素](../extensibility/groups-element.md)|包含定義 VSPackage 的命令群組的項目。|  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)