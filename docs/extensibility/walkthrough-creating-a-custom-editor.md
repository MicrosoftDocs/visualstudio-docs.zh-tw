---
title: 演練:創建自定義編輯器 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7eb376637fd72f3856415ee2527ec622fea02950
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697681"
---
# <a name="walkthrough-create-a-custom-editor"></a>演練:建立自訂編輯器
VSPackage 專案範本可以在C++中創建一個簡單的自定義編輯器。 VSPackage 專案範本不再支援 C# 或可視化基本專案。 有關詳細資訊,請參閱[可視化工作室 SDK](../extensibility/visual-studio-sdk.md)。

## <a name="prerequisites"></a>Prerequisites
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="the-visual-studio-package-project-template"></a>視覺化工作室包項目範本
 您可以在**C++"擴充性"** 資料夾下的「**新項目**」 對話框中找到可視化工作室包專案範本。

### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>使用視覺化工作室套件樣本建立 VS 套件

1. 使用可視化工作室包範本創建專案。

2. 選擇 **「自訂編輯器」** 選項,然後按**下 「下一步**」 。 將顯示 **「編輯器選項」** 頁。

3. 在 **「編輯器名稱」** 方塊鍵入編輯器的名稱。 在 **「檔案副檔名」** 框中鍵入要與編輯器關聯的檔案副檔名。 您的編輯器可用於具有此擴展名的檔案。 檔副檔名僅註冊為 Visual Studio,而不是為 Windows 註冊。 在 **「預設檔名」** 框中鍵入使用編輯器建立的新文件的預設檔名。

4. 按一下 [完成] **** ，在您指定的資料夾中建立 VSPackage。

### <a name="to-test-your-custom-editor"></a>測試自訂編輯器

1. 在 **「檔案」** 選單上,指向 **「新建」** 然後按下「**檔**」。

2. 在 **'新增檔案**'對話框的'**已安裝樣本「** 窗格中,選擇檔案樣本,然後選擇您註冊的檔案類型。

3. 按下 **「打開」** 以查看和編輯文件。

     編輯器支援剪切和貼上、尋找和取代以及打開和關閉和載入操作。

## <a name="see-also"></a>另請參閱
- [VSPackage](../extensibility/internals/vspackages.md)
