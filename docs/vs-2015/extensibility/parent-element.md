---
title: Parent 元素 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2086473bc484fed4e8e351f0c3838074557586c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194085"
---
# <a name="parent-element"></a>Parent 項目
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

按鈕或下拉式方塊的父系可能只是群組。 功能表或群組的父系可以是任何其他功能表或群組。 在 [CommandPlacement 元素](../extensibility/commandplacement-element.md)中，需要這個元素。在其他所有實例中，則是選擇性的。 如果省略這個元素，就會隱含的父系 `Group_Undefined:0` 。  
  
## <a name="syntax"></a>語法  
  
```  
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|guid|必要。 GUID/識別碼命令識別碼的 GUID。|  
|id|必要。 GUID/識別碼命令識別碼的識別碼。|  
  
### <a name="child-elements"></a>子元素  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[CommandTable 元素](../extensibility/commandtable-element.md)|定義代表 VSPackage 提供給整合式開發環境 (IDE) 命令的所有元素。 例如，功能表項目、功能表、工具列和下拉式方塊。|  
|[Buttons 元素](../extensibility/buttons-element.md)|群組 [按鈕元素](../extensibility/button-element.md) 元素。|  
|[Menus 元素](../extensibility/menus-element.md)|定義 VSPackage 所實行的所有功能表。|  
|[Groups 元素](../extensibility/groups-element.md)|包含定義 VSPackage 之命令群組的專案。|  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
