---
title: "點陣圖項目 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: 74652e1b-fcfa-421b-aa9f-fbc081d3b476
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a4db0446a0adeaeee3d3a3fc1c5ae6ee02594f34
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="bitmaps-element"></a>點陣圖項目
群組[點陣圖項目](../extensibility/bitmap-element.md)項目。  
  
## <a name="syntax"></a>語法  
  
```  
<Bitmaps>  
  <Bitmap>... </Bitmap>  
  <Bitmap>... </Bitmap>  
</Bitmaps>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|條件|選擇項。 請參閱[條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|說明|  
|-------------|-----------------|  
|[Bitmaps 元素](../extensibility/bitmaps-element.md)|群組點陣圖項目。|  
|[Bitmap 元素](../extensibility/bitmap-element.md)|定義點陣圖。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[Commands 元素](../extensibility/commands-element.md)|表示 VSPackage 工具列上的命令的集合。|  
  
## <a name="example"></a>範例  
  
```  
<Bitmaps>  
  <Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />  
  <Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"  
    usedList="1, 2, 3, 4"/>  
</Bitmaps>  
```  
  
## <a name="see-also"></a>另請參閱  
 [Vspackage 如何新增使用者介面項目](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [命令、功能表及工具列](../extensibility/internals/commands-menus-and-toolbars.md)