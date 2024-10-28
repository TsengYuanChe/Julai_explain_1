# Explaining Julia program

# Monty Hall Problem Simulation

此專案為一個用 Julia 撰寫的程式，模擬著名的 Monty Hall 問題，並比較「更換選擇」與「堅持原選擇」策略的勝率。

## 程式說明

### `play_game` 函數

```julia
# 定義單一遊戲模擬函數
function play_game(switch::Bool)
    # 隨機決定車子的門
    car_behind_door = rand(1:3)
    
    # 參賽者的初始選擇
    initial_choice = rand(1:3)
    
    # 主持人打開一扇沒有車的門
    possible_doors = [1, 2, 3]
    possible_doors = setdiff(possible_doors, [initial_choice])

    if car_behind_door in possible_doors
        host_opens = setdiff(possible_doors, [car_behind_door])[1]
    else
        host_opens = possible_doors[1]
    end
    
    # 如果參賽者選擇更換門，將最終選擇改為剩餘的門
    remaining_doors = setdiff([1, 2, 3], [initial_choice, host_opens])
    final_choice = switch ? remaining_doors[1] : initial_choice
    
    # 回傳是否選擇到有車的門
    return final_choice == car_behind_door
end
