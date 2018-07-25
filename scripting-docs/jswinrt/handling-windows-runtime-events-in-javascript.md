---
title: 在 JavaScript 中處理 Windows 執行階段事件 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime events
- Windows Runtime events [JavaScript]
ms.assetid: d9436aff-2c30-4846-b8df-eaa3e63fd75c
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7e5780a2462e8980c22c474ae6236c87aee599b
ms.sourcegitcommit: 498e39e89a89ad7bf9dcb0617424fff999b1c3b2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/21/2018
ms.locfileid: "36302803"
---
# <a name="handling-windows-runtime-events-in-javascript"></a>在 JavaScript 中處理 Windows 執行階段事件
Windows 執行階段事件在 JavaScript 中的表示方式，不同於在 C++ 或 .NET Framework 中的表示方式。 這些事件不是類別屬性，而會以傳遞至類別的 `addEventListener` 和 `removeEventListener` 方法的 (小寫) 字串識別碼表示。 例如，您可以將字串 "positionchanged" 傳遞給 `Geolocator.addEventListener` 方法，以新增 [Geolocator.PositionChanged](https://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.geolocation.geolocator.positionchanged.aspx) 事件的事件處理常式：  
  
```JavaScript  
var locator = new Windows.Devices.Geolocation.Geolocator();  
locator.addEventListener(  
    "positionchanged",   
     function (ev) {  
        console.log("Got event");  
    });  
```  
  
 您也可以設定 `locator.onpositionchanged` 屬性：  
  
```JavaScript  
locator.onpositionchanged =    
    function (ev) {  
        console.log("Got event");  
    };  
```  
  
.NET/C++ 與 JavaScript 的另一個差異是事件處理常式所採用的參數數目。 在 .NET/C++ 中，處理常式會採用兩個項目：事件傳送者和事件資料。 在 JavaScript 中，這兩個會組合為單一 `Event` 物件。 在下列範例中，`ev` 參數同時包含事件傳送者 (`target` 屬性) 和事件資料屬性 (這裡就是 `position`)。 事件資料屬性是針對每個事件記錄的屬性。
  
```JavaScript  
function (ev) {  
    console.log("Sender: " + ev.target);  
    console.log("Position: " +  
        ev.position.latitude + "," +  
        ev.position.longitude);  
};  
```  
  
> [!IMPORTANT]
>  在 Internet Explorer 中執行的應用程式無法使用 Windows 執行階段功能。  
  
## <a name="see-also"></a>請參閱  
 [在 JavaScript 中使用 Windows 執行階段](../jswinrt/using-the-windows-runtime-in-javascript.md)
