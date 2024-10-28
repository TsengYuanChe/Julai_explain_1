# Monty Hall Problem Simulation

此專案以 Julia 撰寫，用來模擬 Monty Hall 問題，並比較「更換選擇」與「堅持原選擇」策略的勝率。

## 專案說明

Monty Hall 問題是個著名的機率問題，參賽者從三扇門中選擇一扇，後來主持人會打開一扇沒有車的門，接著參賽者可以選擇是否更換選擇。此模擬程式透過多次遊戲來展示「更換選擇」策略的優勢。

### 程式邏輯概述

- **play_game(switch)**：模擬一次遊戲，根據 `switch` 判斷參賽者是否更換選擇，並返回是否選到車。
  - 隨機選擇車的位置與參賽者的初始選擇。
  - 主持人選擇一扇沒有車的門並打開。
  - 根據 `switch` 判斷最終選擇，並返回結果。

- **run_simulation(num_trials, switch)**：執行多次遊戲並計算勝率。
  - 透過指定的 `num_trials` 執行多次 `play_game`，並計算勝利次數，返回勝率。

### 使用範例

```julia
num_trials = 10000
stick_win_rate = run_simulation(num_trials, false)
switch_win_rate = run_simulation(num_trials, true)

println("Probability of winning if you stick with your initial choice: ", stick_win_rate)
println("Probability of winning if you switch: ", switch_win_rate)

