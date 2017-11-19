---
title: "如何： 搭配 ARM 裝置使用圖形診斷 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 346fd3c0-9e92-4ab8-bb3b-1aa9000a2483
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 60898b7ea37c7e732453fd03f9c557b2494f66c5
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2017
---
# <a name="how-to-use-graphics-diagnostics-with-an-arm-device"></a>如何：搭配 ARM 裝置使用圖形診斷
圖形診斷支援遠端偵錯 ARM 裝置上的 Direct3D 應用程式，且 ARM 裝置執行 Windows RT 8.1 或 Windows Phone 8.1。 您可以從在裝置上執行的 Direct3D 應用程式擷取圖形資訊，或使用裝置做為先前擷取之圖形資訊的播放電腦。  
  
## <a name="using-graphics-diagnostics-with-an-arm-based-device"></a>搭配 ARM 裝置使用圖形診斷  
 因為 Visual Studio 未在 ARM 裝置上執行，所以您需要使用遠端偵錯工具來分析在其上執行的應用程式。 遠端偵錯工具支援圖形擷取和播放，讓您可以診斷呈現錯誤，並評估這些裝置的圖形效能，就像您可以偵錯裝置上的應用程式一樣地輕鬆。  
  
 若要使用圖形診斷功能，請先在裝置上啟用遠端偵錯。  
  
#### <a name="to-enable-remote-debugging-on-your-arm-based-device"></a>在 ARM 裝置上啟用遠端偵錯  
  
1.  安裝[ARM 套件原則](http://msdn.microsoft.com/windows/desktop/dn469188)arm 裝置上。  
  
2.  安裝[遠端偵錯工具](http://go.microsoft.com/fwlink/?LinkId=393086)arm 裝置上。  
  
> [!IMPORTANT]
>  您可能需要針對 Windows Phone 8.1 裝置，註冊您的電話以進行開發。 若要這麼做，您必須是註冊的開發人員。 如需詳細資訊，請參閱[如何部署和執行應用程式 Windows Phone 8](http://msdn.microsoft.com/library/windowsphone/develop/ff402565.aspx)。  
  
 在裝置上啟用遠端偵錯之後，請將它設為偵錯目標，並啟動圖形診斷。  
  
#### <a name="to-configure-and-start-graphics-diagnostics-on-your-device"></a>在裝置上設定和啟動圖形診斷  
  
1.  在**方案平台**下拉式清單中，選取**ARM** ，讓 arm 裝置可以做為遠端偵錯目標。  
  
2.  在**偵錯目標**下拉式清單中，選取 ARM 裝置。  
  
3.  在功能表上，選擇 **偵錯**，**圖形**，**開始診斷**。 (鍵盤：Alt+F5)  
  
## <a name="see-also"></a>另請參閱  
 [在遠端電腦上執行的 UWP 應用程式](../run-windows-store-apps-on-a-remote-machine.md)   
 [如何：變更圖形診斷播放電腦](how-to-change-the-graphics-diagnostics-playback-machine.md)