---
title: 逐步解說：使用C#或 VISUAL BASIC 建立 SDK |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a604e3500c0ea438c987c4cf07ded98a5e03dd61
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2020
ms.locfileid: "77558215"
---
# <a name="walkthrough-creating-an-sdk-using-c-or-visual-basic"></a>逐步解說︰使用 C# 或 Visual Basic 建立 SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在本逐步解說中，您將瞭解如何使用視覺效果C#來建立簡單的數學程式庫 sdk，然後將 SDK 封裝為 Visual Studio 擴充功能（VSIX）。 您將完成下列程式：  
  
- [若要建立 SimpleMath Windows 執行階段元件](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)  
  
- [若要建立 SimpleMathVSIX 擴充功能專案](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)  
  
- [建立使用類別庫的範例應用程式](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)  
  
## <a name="prerequisites"></a>Prerequisites  
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱[VISUAL STUDIO SDK](../extensibility/visual-studio-sdk.md)。  
  
## <a name="createClassLibrary"></a>若要建立 SimpleMath Windows 執行階段元件  
  
1. 在功能表列上，選擇 [檔案]、[**新增** **]、[** **新增專案**]。  
  
2. 在範本清單中，展開 [**視覺C#效果**] 或 [ **Visual Basic**]，選擇 [ **Windows 儲存區**] 節點，然後選擇 [ **Windows 執行階段元件**] 範本。  
  
3. 在 [**名稱**] 方塊中，指定**SimpleMath**，然後選擇 [**確定]** 按鈕。  
  
4. 在**方案總管**中，開啟**SimpleMath**專案節點的快捷方式功能表，然後選擇 [**屬性**]。  
  
5. 將**Class1.cs**重新命名為**Arithmetic.cs** ，並加以更新以符合下列程式碼：  
  
     [!code-csharp[CreatingAnSDKUsingWinRT#3](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmath/arithmetic.cs#3)]
     [!code-vb[CreatingAnSDKUsingWinRT#3](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmath/arithmetic.vb#3)]  
  
6. 在**方案總管**中，開啟 [**方案 ' SimpleMath '** ] 節點的快捷方式功能表，然後選擇 [ **Configuration Manager**]。  
  
     [ **Configuration Manager** ] 對話方塊隨即開啟。  
  
7. 在 [使用中的**方案**設定] 清單中，選擇 [**發行**]。  
  
8. 在 [**設定**] 欄中，確認 [ **SimpleMath** row] 已設為 [**發行**]，然後選擇 [**關閉**] 按鈕以接受變更。  
  
    > [!IMPORTANT]
    > SimpleMath 元件的 SDK 僅包含一個設定。 此設定必須是發行組建，或使用元件的應用程式不會通過[!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)]的認證。  
  
9. 在**方案總管**中，開啟**SimpleMath**專案節點的快捷方式功能表，然後選擇 [**組建**]。  
  
## <a name="createVSIX"></a>若要建立 SimpleMathVSIX 擴充功能專案  
  
1. 在 [**方案 ' SimpleMath '** ] 節點的快捷方式功能表上，選擇 [**加入**]、[**新增專案**]。  
  
2. 在範本清單中，展開 [**視覺C#效果**] 或 [ **Visual Basic**]，選擇 [擴充性 **] 節點，** 然後選擇 [ **VSIX 專案**] 範本。  
  
3. 在 [**名稱**] 方塊中，指定**SimpleMathVSIX**，然後選擇 [**確定]** 按鈕。  
  
4. 在**方案總管**中，選擇**extension.vsixmanifest**專案。  
  
5. 在功能表列上選擇 [檢視]、[程式碼]。  
  
6. 以下列 XML 取代現有的 XML：  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]
  
7. 在**方案總管**中，選擇 [ **SimpleMathVSIX** ] 專案。  
  
8. 在功能表列上，選擇 [**專案**]、[**加入新專案**]。  
  
9. 在**一般專案**清單中，展開 [**資料**]，然後選擇 [ **XML**檔案]。  
  
10. 在 [**名稱**] 方塊中，指定 `SDKManifest.xml`，然後選擇 [**新增**] 按鈕。  
  
11. 在**方案總管**中，開啟 `SDKManifest.xml`的快捷方式功能表，選擇 [**屬性**]，然後將 [**在 VSIX 中包含**] 屬性的值變更為**True**。  
  
12. 以下列 XML 取代檔案的內容：  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmathvsix/sdkmanifest.xml#1)]
     [!code-xml[CreatingAnSDKUsingWinRT#1](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmathvsix/sdkmanifest.xml#1)]  
  
13. 在**方案總管**中，開啟**SimpleMathVSIX**專案的快捷方式功能表，選擇 [**加入**]，然後選擇 [**新增資料夾**]。  
  
14. 將資料夾重新命名為 `references`。  
  
15. 開啟 [**參考**] 資料夾的快捷方式功能表，選擇 [**加入**]，然後選擇 [**新增資料夾**]。  
  
16. 將子資料夾重新命名為 `commonconfiguration`，在其中建立子資料夾，並將子資料夾命名為 `neutral`。  
  
17. 重複前面四個步驟，這次將第一個資料夾重新命名為 `redist`。  
  
     專案現在包含下列資料夾結構：  
  
    ```  
    references\commonconfiguration\neutral  
    redist\commonconfiguration\neutral  
    ```  
  
18. 在**方案總管**中，開啟**SimpleMath**專案的快捷方式功能表，然後選擇 [**在檔案瀏覽器中開啟資料夾**]。  
  
19. 在 [檔案**管理器**] 中，流覽至 [bin\Release] 資料夾，開啟 SimpleMath 檔案的快捷方式功能表，然後選擇 [**複製**]。  
  
20. 在**方案總管**中，將檔案貼入**SimpleMathVSIX**專案的 references\commonconfiguration\neutral 資料夾中。  
  
21. 重複上一個步驟，將 SimpleMath 檔案貼入**SimpleMathVSIX**專案的 redist\commonconfiguration\neutral 資料夾中。  
  
22. 在**方案總管**中，選擇 [ **SimpleMath**]。  
  
23. 在功能表列上，選擇 [**視圖**]、[**屬性**] （鍵盤：選擇 F4 鍵）。  
  
24. 在 [**屬性**] 視窗中，將 [**組建動作**] 屬性變更為 [**內容**]，然後將 [**在 VSIX 中包含**] 屬性變更為 [ **True**]。  
  
25. 在**方案總管**中，針對**SimpleMath**重複此程式。  
  
26. 在**方案總管**中，選擇 [ **SimpleMathVSIX** ] 專案。  
  
27. 在功能表列上，選擇 [**組建**]、[**組建 SimpleMathVSIX**]。  
  
28. 在**方案總管**中，開啟**SimpleMathVSIX**專案的快捷方式功能表，然後選擇 [**在檔案瀏覽器中開啟資料夾**]。  
  
29. 在 [檔案**管理器**] 中，流覽至 \bin\Release 資料夾，然後執行 SimpleMathVSIX 以安裝它。  
  
30. 選擇 [**安裝**] 按鈕，等待安裝完成，然後重新開機 Visual Studio。  
  
## <a name="createSample"></a>建立使用類別庫的範例應用程式  
  
1. 在功能表列上，選擇 [檔案]、[**新增** **]、[** **新增專案**]。  
  
2. 在範本清單中，展開 [**視覺C#效果**] 或 [ **Visual Basic**]，然後選擇 [ **Windows Store** ] 節點。  
  
3. 選擇 [**空白應用程式**] 範本，將專案命名為**ArithmeticUI**，然後選擇 [**確定]** 按鈕。  
  
4. 在**方案總管**中，開啟**ArithmeticUI**專案的快捷方式功能表，然後選擇 [**加入**]、[**參考**]。  
  
5. 在參考型別清單中，展開 [ **Windows**]，然後選擇 [**擴充**功能]。  
  
6. 在詳細資料窗格中，選擇 [**簡單數學 SDK** ] 延伸模組。  
  
    SDK 的其他相關資訊隨即出現。 您可以選擇 [**更多資訊**] 連結來開啟 https://docs.microsoft.com，如同您稍早在本逐步解說中的 sdkmanifest.xml 所指定。  
  
7. 在 [**參考管理員**] 對話方塊中，選取 [**簡單數學 SDK** ] 核取方塊，然後選擇 [**確定]** 按鈕。  
  
8. 在功能表列上，選擇 [ **View**]、[**物件瀏覽器**]。  
  
9. 在 [**流覽]** 清單中，選擇 [ **Simple Math**]。  
  
     您現在可以探索 SDK 的內容。  
  
10. 在**方案總管**中，開啟 MainPage，並將其內容取代為下列 xaml：  
  
     [!code-xml[CreatingAnSDKUsingWinRTDemoApp#1](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/cs/winrtmathtest/mainpage.xaml#1)]
     [!code-xml[CreatingAnSDKUsingWinRTDemoApp#1](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/vb/winrtmathtest/mainpage.xaml#1)]  
  
11. 更新 MainPage.xaml.cs 以符合下列程式碼：  
  
     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/cs/winrtmathtest/mainpage.xaml.cs#2)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/vb/winrtmathtest/mainpage.xaml.vb#2)]  
  
12. 選擇 F5 鍵以執行應用程式。  
  
13. 在應用程式中，輸入任兩個數字，選擇一項作業，然後選擇 [ **=** ] 按鈕。  
  
     正確的結果隨即出現。  
  
    您已成功建立並使用延伸模組 SDK。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說：使用C++  建立 SDK](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)  
 [逐步解說：使用 JavaScript 建立 SDK](walkthrough-creating-an-sdk-using-javascript.md)   
 [建立軟體開發套件](../extensibility/creating-a-software-development-kit.md)
