---
title: 疑難排解：如何? 發行現有擴充功能的新版本？
description: 透過發行工作流程更新現有擴充功能的指南。
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/14/2020
ms.technology: vs-ide-general
ms.assetid: 5DA76197-7859-421f-AC45-401F22F5D794
ms.topic: troubleshooting
ms.openlocfilehash: 862ae404571da44d9ca28db2c94d2ebeb39ce79f
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97488460"
---
# <a name="troubleshooting-how-do-i-release-a-new-version-of-my-existing-extension"></a>疑難排解：如何? 發行現有擴充功能的新版本？

> [!IMPORTANT]
> 目前，在 Mac 的 Visual Studio 2019 中未正式支援建立新的擴充功能。

Visual Studio for Mac 擴充功能存放庫伺服器將在2021年1月15日移動。 此移動並不會影響已下載您延伸模組的使用者，但會變更您在這個日期之後發佈延伸模組的新版本的方式。

作為現有擴充功能的作者，您必須遵循不同的工作流程來發行進一步的更新。 此程序包含：
- 設定每個延伸模組的公用 GitHub 存放庫
- 透過[延伸模組發行郵寄清單](mailto:vsmextpub@microsoft.com)，將存放庫 URL 共用至 Visual Studio for Mac 小組
- 使用 GitHub 中的發行功能來更新您的延伸模組


## <a name="initial-setup"></a>初始設定 

若要繼續將更新發佈至您的延伸模組，您必須建立公用 GitHub 存放庫。 如果您發行多個擴充功能，則每個延伸模組都必須有個別的存放庫，除非您一律將它們設為版本並加以發佈，在這種情況下，您可以使用單一存放庫。

> [!NOTE]
> 雖然您延伸模組的 GitHub 存放庫必須是公用的，但您不需要在該處裝載任何程式碼。 完成此程式後，您就不需要在 GitHub 中擁有任何程式碼。


## <a name="share-the-location-of-your-repository"></a>共用您存放庫的位置

設定存放庫之後，請使用 URL 將電子郵件傳送給 [延伸模組發行郵寄清單](mailto:vsmextpub@microsoft.com) 。


## <a name="release-a-new-version"></a>發行新版本

您將使用存放庫主頁面上的 [建立新發行] 連結來開始更新擴充功能的程式。 選取該連結之後，請遵循下列步驟：

1. 以下列格式將資訊新增至版本的 **標記版本**

    > v \<releaseVersion> \- vsm\<targetVersion>

    其中：
     - **&lt; releaseVersion &gt;** 是您的延伸模組版本號碼
     - **&lt; targetVersion &gt;** 是您的延伸模組目標 Visual Studio for Mac 的最小版本

2.  (選擇性) [ **標題** ] 和 [ **描述** ] 欄位可以填入您想要的任何資訊;此工作流程不會使用這些欄位中的資訊。

3. 確定未 **核取 [發行前版本** ] 核取方塊。 若已核取此項，將不會由此發行程式挑選。

4. 將 mpack 檔案附加至在 **二進位** 區段中執行擴充功能的檔案 (s) 。 您可以在發行中附加多個 **mpack** 檔案。

Visual Studio for Mac 會顯示您的延伸模組的最新版本，其與用來存取擴充功能存放庫的 Visual Studio for Mac 安裝相容。

只要您向 Visual Studio for Mac 團隊註冊您的 GitHub 存放庫，您的延伸模組版本將會在24小時內由 Visual Studio for Mac 挑選。

## <a name="additional-information"></a>其他資訊

- 不符合上述所述需求的版本不會發行。 
- 2021年1月15日之後，擴充功能更新將只會顯示在 Visual Studio for Mac 8.0 或更新版本中。
- 現有的延伸模組將持續提供給 Visual Studio for Mac 使用者使用，而不會有任何動作。 如果您在2021年1月15日之後發行新版本，則只需要遵循本指南中的指示。
