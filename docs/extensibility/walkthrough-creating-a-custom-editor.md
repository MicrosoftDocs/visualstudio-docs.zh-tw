---
title: 逐步解說：建立自訂編輯器 |Microsoft Docs
description: 瞭解 VSPackage 專案範本如何使用此逐步解說，在 c + + 中建立簡單的自訂編輯器。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 188c02471e8921e66faefe9668ec3f54c935b50b
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863128"
---
# <a name="walkthrough-create-a-custom-editor"></a>逐步解說：建立自訂編輯器
VSPackage 專案範本可以在 c + + 中建立簡單的自訂編輯器。 VSPackage 專案範本不再支援 c # 或 Visual Basic 專案。 如需詳細資訊，請參閱 [VISUAL STUDIO SDK](../extensibility/visual-studio-sdk.md)。

## <a name="prerequisites"></a>必要條件
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="the-visual-studio-package-project-template"></a>Visual Studio 套件專案範本
 您可以在 [ **新增專案** ] 對話方塊的 [ **c + +** 擴充性] 資料夾下找到 Visual Studio 套件專案範本。

### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>使用 Visual Studio 套件範本建立 VSPackage

1. 使用 Visual Studio 套件範本建立專案。

2. 選取 [ **自訂編輯器** ] 選項，然後按 **[下一步]**。 編輯器的 [ **選項** ] 頁面隨即出現。

3. 在 [ **編輯器名稱** ] 方塊中輸入編輯器的名稱。 在 [ **副檔名** ] 方塊中，輸入您要與編輯器相關聯的副檔名。 您的編輯器適用于具有此副檔名的檔案。 副檔名僅針對 Visual Studio 註冊，不適用於 Windows。 在 [ **預設檔案名** ] 方塊中，輸入使用編輯器建立之新檔的預設檔案名。

4. 按一下 [完成]  ，在您指定的資料夾中建立 VSPackage。

### <a name="to-test-your-custom-editor"></a>測試自訂編輯器

1. **在 [檔案**] 功能表上，指向 [**新增**]，**然後按一下 [** 檔案]。

2. 在 [**新增** 檔案] 對話方塊的 [**已安裝的範本**] 窗格中，選取 [檔案] 範本，然後選取您註冊的檔案類型。

3. 按一下 [ **開啟** ] 以查看和編輯檔。

     編輯器支援剪下和貼上、尋找和取代，以及開啟和載入作業。

## <a name="see-also"></a>請參閱
- [VSPackages](../extensibility/internals/vspackages.md)
