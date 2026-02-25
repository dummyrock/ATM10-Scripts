-- ATM10 Item Transfer Script
-- Simple version for ComputerCraft

local function listInventories()
    print("\nConnected inventories:")
    for _, side in ipairs(rs.getSides()) do
        if peripheral.isPresent(side) then
            print("  - " .. side)
        end
    end
end

local function moveItems(sourceSide, destSide)
    local source = peripheral.wrap(sourceSide)
    local dest = peripheral.wrap(destSide)
    
    if source == nil or dest == nil then
        print("Error: Invalid inventory side")
        return
    end
    
    print("Moving items from " .. sourceSide .. " to " .. destSide)
    
    local items = source.list()
    local count = 0
    
    for slot, item in pairs(items) do
        source.pushItems(destSide, slot)
        count = count + item.count
    end
    
    print("Transferred " .. count .. " items")
end

local function moveSpecificItem(sourceSide, destSide, itemName)
    local source = peripheral.wrap(sourceSide)
    local dest = peripheral.wrap(destSide)
    
    if source == nil or dest == nil then
        print("Error: Invalid inventory side")
        return
    end
    
    print("Moving " .. itemName .. " from " .. sourceSide .. " to " .. destSide)
    
    local items = source.list()
    local count = 0
    
    for slot, item in pairs(items) do
        if item.name == itemName then
            source.pushItems(destSide, slot)
            count = count + item.count
        end
    end
    
    print("Transferred " .. count .. " items of type " .. itemName)
end

-- Main loop
while true do
    print("\n=== ATM10 Item Mover ===")
    print("1. List inventories")
    print("2. Move all items")
    print("3. Move specific item")
    print("4. Exit")
    write("Choose: ")
    
    local choice = io.read()
    
    if choice == "1" then
        listInventories()
    elseif choice == "2" then
        write("From side: ")
        local from = io.read()
        write("To side: ")
        local to = io.read()
        moveItems(from, to)
    elseif choice == "3" then
        write("From side: ")
        local from = io.read()
        write("To side: ")
        local to = io.read()
        write("Item name: ")
        local item = io.read()
        moveSpecificItem(from, to, item)
    elseif choice == "4" then
        print("Exiting...")
        break
    end
end

