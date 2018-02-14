---
title: "Android 偵錯工具屬性 (C++) | Microsoft Docs"
ms.custom: 
ms.date: 10/23/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-mobile
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 789f7a1c-38b4-41d0-809b-14f4d96c8116
author: corob
ms.author: mblome
manager: ghogen
f1_keywords:
- VC.Project.AndroidDebugger.DebuggerType
- VC.Project.AndroidDebugger.AndroidDeviceID
- VC.Project.AndroidDebugger.PackagePath
- VC.Project.AndroidDebugger.LaunchActivity
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 3ca25e560a4bc3060d86972b4000b3d9ad59ba1f
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="android-debugger-properties"></a>Android 偵錯工具屬性

屬性 | 描述 | 選擇
--- | ---| ---
偵錯工具類型 | 指定要偵錯的程式碼類型。 | **僅限原生**<br>**僅限 Java**<br>
偵錯目標 | 指定要用於偵錯的模擬器或裝置。 如果沒有模擬器正在執行中，請使用 'Android Virtual Device (AVD) Manager' 啟動裝置。
要啟動的套件 | 指定將進行偵錯的 .apk 位置。 選擇這個選項可指定在偵錯應用程式時應該啟動的特定套件 (APK)。
啟動活動 | 您用於啟動應用程式的 Android 活動必須與資訊清單中所使用的活動相符。 按 [套用] 以從 AndroidManifest.xml 擷取清單並動態填入。
其他符號搜尋路徑 | 偵錯符號的其他搜尋路徑。
Java 原始程式檔的其他搜尋路徑 | Java 原始程式檔的其他搜尋路徑  (僅適用於當偵錯工具類型為僅限 Java 時)。
