---
title: Bitmap 元素 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fc1fb57c7ec43421b211b29cfd6ab97b24a1864c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184738"
---
# <a name="bitmap-element"></a>Bitmap 項目
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

定義點陣圖。 點陣圖是從資源或檔案載入的。  
  
## <a name="syntax"></a>語法  
  
```  
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|guid|必要。 GUID/識別碼命令識別碼的 GUID。<br /><br /> 點陣圖的 guid 屬性與任何 VSPackage 或其他命令群組沒有關聯。  它應該是點陣圖定義的唯一的，而且不應該用於任何其他用途。|  
|渣 油|GUID/識別碼命令識別碼的識別碼。 必須是 resID 或 href 屬性。<br /><br /> ResID 屬性是一個整數資源識別碼，可決定要在命令表格合併期間載入的點陣圖區。  載入命令資料表時，將會從相同模組的資源載入資源識別碼所指定的點陣圖。|  
|usedList|如果 resID 屬性存在，則為必要項。 選取點陣圖條紋中的可用影像。|  
|href|點陣圖的路徑。 必須是 resID 或 href 屬性。<br /><br /> 會搜尋包含路徑中指出的影像檔案，並將其內嵌在產生的二進位檔中。  在命令表格合併期間，會複製影像，而不需要額外的資源查閱或載入。  如果 usedList 屬性不存在，則會提供帶狀中的所有影像。 **注意：**  影像可能會以數種格式提供，包括 .bmp、.png 和 .gif。  舊版編譯器不支援具有部分透明度之 Alpha 資訊的32位點陣圖影像。 這些版本的因應措施是使用 .png 格式。|  
|條件|選擇性。 請參閱 [條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[Bitmaps 元素](../extensibility/bitmaps-element.md)|群組點陣圖元素。|  
  
## <a name="example"></a>範例  
  
```  
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />  
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"  
  usedList="1, 2, 3, 4"/>  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
