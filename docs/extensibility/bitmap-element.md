---
title: Bitmap 元素 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dbdd61e22a392309c45005c0e183704c6b84040c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53879367"
---
# <a name="bitmap-element"></a>Bitmap 元素
定義點陣圖。 從資源或者從檔案載入點陣圖。  
  
## <a name="syntax"></a>語法  
  
```  
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和元素  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|guid|必要項。 GUID/識別碼命令識別碼的 GUID。<br /><br /> 無法與任何 VSPackage 或其他命令群組相關聯的點陣圖的 guid 屬性。  它應該是唯一之點陣圖定義，且不應用於其他用途。|  
|resID|GUID/識別碼的命令識別項的識別碼。 需要 resID 或 href 屬性。<br /><br /> ResID 屬性會決定要載入命令資料表合併期間點陣圖區整數資源識別碼。  載入命令資料表時，會從相同模組的資源載入的資源識別碼所指定的點陣圖。|  
|usedList|需要 resID 屬性是否存在。 選取可用的映像中的點陣圖區。|  
|href|點陣圖的路徑。 需要 resID 或 href 屬性。<br /><br /> 指定的映像檔，內嵌在產生的二進位檔中搜尋 include 路徑。  在命令資料表合併期間複製映像，並不需要任何額外的資源查閱或負載。  UsedList 屬性不存在，在區域中的所有映像可用。 **注意：** 映像可能會提供包含數種格式之一 *.bmp*， *.png*，並 *.gif*。  舊版編譯器不支援部分的透明度的 alpha 資訊的 32 位元點陣圖影像。 這些版本的因應措施是使用 *.png*格式。|  
|條件|選擇性。 請參閱[條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[Bitmaps 元素](../extensibility/bitmaps-element.md)|分組點陣圖項目。|  
  
## <a name="example"></a>範例  
  
```  
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />  
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"  
  usedList="1, 2, 3, 4"/>  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令表檔案 (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)