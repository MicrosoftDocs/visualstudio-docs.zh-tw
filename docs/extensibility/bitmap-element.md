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
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: eb265aabdb4feda05512e036cda19abc574e2fd4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="bitmap-element"></a>點陣圖項目
定義點陣圖。 點陣圖從資源，或是從檔案載入。  
  
## <a name="syntax"></a>語法  
  
```  
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|Guid|必要。 GUID/識別碼命令識別碼的 GUID。<br /><br /> 無法與任何 VSPackage 或其他命令群組 guid 屬性的點陣圖。  它應該是唯一點陣圖定義，且不應用於其他用途。|  
|resID|GUID/識別碼命令識別項的識別碼。 需要 resID 或 href 屬性。<br /><br /> ResID 屬性會決定是要載入期間合併的命令資料表的點陣圖帶整數資源 ID。  載入的命令資料表時，就會從相同的模組資源載入資源識別碼所指定的點陣圖。|  
|usedList|需要 resID 屬性是否存在。 選取可用的映像區域中的點陣圖。|  
|href|點陣圖的路徑。 需要 resID 或 href 屬性。<br /><br /> 指定的影像檔案，這個檔案內嵌在產生的二進位搜尋 include 路徑。  在命令資料表合併，影像會複製並不需要任何額外的資源查閱或負載。  如果 usedList 屬性不存在，則在區域中的所有映像。 **注意：**中包括.bmp、.png 和.gif 的幾種格式之一可能提供的映像。  舊版編譯器不支援 alpha 資訊部分透明度的 32 位元點陣圖影像。 這些版本的因應措施是使用.png 格式。|  
|條件|選擇性。 請參閱[條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[Bitmaps 元素](../extensibility/bitmaps-element.md)|群組點陣圖項目。|  
  
## <a name="example"></a>範例  
  
```  
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />  
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"  
  usedList="1, 2, 3, 4"/>  
```  
  
## <a name="see-also"></a>請參閱  
 [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)