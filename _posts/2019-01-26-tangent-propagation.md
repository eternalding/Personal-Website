---
layout: post
author: Eternalding
title: "Tangent Propagation"
---

 <font color=#7B68EE size=7>Tangent Propagation</font>
 ========================================================
本文圖片均來自Bishop - Pattern Recognition and Machine Learning , 2006 Spring. All rights reserved.

# __Introduction__

  在 pattern recognition 過程中，我們往往會利用一些手段，例如 regularization，來處理 input 的 transformation。  

  例如在做數字手寫辨識時，假如原先的input是數字"6"，當我對這張圖片做了 transformation (例如把數字寫大一點、寫在左上 or 右下...etc)，理論上 network 所做的 prediction 結果不應該有差異，因為還是數字"6"，這種特性又稱為invariant。  

  但以資料的角度來看，儘管都是6，已經產生巨大的變化了，為了保持 prediction 的 invariant，有許多種作法，其中一種就是利用 regularization，使得 input 的變化不影響 weight 太多，這也是 tangent propagation 的核心概念。

# __Tangent Propagation__

  首先給定 input vector X<sub>n</sub>，並對其做 continuous transformaion(例如旋轉)，則 X<sub>n</sub> 將在 D-dimension的空間中，掃出一個manifold(流型) *M*，如下圖:  
  <center>![salkdfhgol](/assets/tangent_propagation/1-1.jpg)</center>
  <center>D=2的例子</center>

  假定這個 continuous transformation 只受到單一變量 $\Xi$ 的影響，例如旋轉的角度，則 *M* 是一個一  
  $$ evidence\_{i}=\sum\_{j}W\_{ij}x\_{j}+b\_{i} $$
