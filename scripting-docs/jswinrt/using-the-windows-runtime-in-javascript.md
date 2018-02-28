---
title: "在 JavaScript 中使用 Windows 執行階段 | Microsoft Docs"
ms.custom: 
ms.date: 02/03/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime
ms.assetid: 90658546-f746-4e34-a7d1-71cf9ee322a2
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c81f5d83056ceb87987e263f09c0d5e5017dbb6f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="using-the-windows-runtime-in-javascript"></a>在 JavaScript 中使用 Windows 執行階段
當您撰寫通用 Windows 平台 (UWP) 應用程式時，您可以透過使用原生 JavaScript 物件、方法和屬性的大致相同方式，來使用 Windows 執行階段類別、方法和屬性。 本主題提供簡介資訊及說明在 JavaScript 中使用 Windows 執行階段應用程式開發介面之基本概念的主題連結，包括如何表示 Windows 執行階段類型、如何使用非同步 Windows 執行階段方法，以及如何接聽和處理 Windows 執行階段事件等的說明。  
  
 您可在 [JavaScript 語言參考](../javascript/javascript-language-reference.md)找到 JavaScript 參考文件。  
  
> [!IMPORTANT]
>  在 Internet Explorer 中執行的應用程式無法使用 Windows 執行階段功能。  
  
## <a name="windows-runtime-reference-documentation"></a>Windows 執行階段參考文件  
 如需參考文件，請參閱 [Windows 執行階段參考](https://msdn.microsoft.com/en-us/library/windows/apps/br211377.aspx)。 該文件提供 JavaScript 以及 C++、C# 和 Visual Basic 的程式碼範例。  
  
## <a name="writing-windows-runtime-components-in-c-c-or-visual-basic"></a>以 C++、C# 或 Visual Basic 撰寫 Windows 執行階段元件  
 如需撰寫 JavaScript 可以使用之 Windows 執行階段元件的指示和指導方針，請參閱[在 C++ 中建立 Windows 執行階段元件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)和[在 C# 和 Visual Basic 中建立 Windows 執行階段元件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic)。  
  
## <a name="casing-conventions-with-windows-runtime-features"></a>Windows 執行階段功能的大小寫慣例  
 在 JavaScript 中的 Windows 執行階段功能大小寫慣例與其他語言稍有不同：  
  
-   命名空間和類別是 Pascal 命名法：  
  
    ```JavaScript  
    Windows.Deployment.PackageInfo;  
    ```  
  
-   類別的成員 (包括方法和屬性) 以及結構和列舉的成員是駝峰式命名法：  
  
    ```JavaScript  
    Deployment.PackageInfo.createPackage();  
    ```  
  
-   事件名稱是小寫：  
  
    ```JavaScript  
    dataTransferManager.ontargetapplicationchosen;  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [使用 Windows 執行階段 API 時的考量](../jswinrt/considerations-when-using-the-windows-runtime-api.md)   
 [使用 Windows 執行階段非同步方法](../jswinrt/using-windows-runtime-asynchronous-methods.md)   
 [在 JavaScript 中處理 Windows 執行階段事件](../jswinrt/handling-windows-runtime-events-in-javascript.md)   
 [以 JavaScript 表示 Windows 執行階段類型](../jswinrt/javascript-representation-of-windows-runtime-types.md)   
 [Windows 執行階段 DateTime 和 TimeSpan 的 JavaScript 投影](../jswinrt/windows-runtime-datetime-and-timespan-representations.md)