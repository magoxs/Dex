-- Código Exemplo de DEX
local function loadDex()
    local Dex = game:GetObjects("rbxassetid://3567096419")[1]
    Dex.Parent = game.CoreGui
    local function load(Obj, Url)
        local function GiveOwnGlobals(Func, Env)
            local Fenv = getfenv(Func)
            local RealFenv = {}
            for Index, Value in next, Fenv do
                RealFenv[Index] = Value
            end
            for Index, Value in next, Env do
                RealFenv[Index] = Value
            end
            setfenv(Func, RealFenv)
            return Func
        end
        local function LoadScripts(Xml)
            local function RunFunction(Func, Script)
                local function RunScript(Script)
                    local Fenv = getfenv(Script)
                    local RealFenv = {}
                    for Index, Value in next, Fenv do
                        RealFenv[Index] = Value
                    end
                    setfenv(Script, RealFenv)
                    pcall(Script)
                end
                if type(Func) == "function" then
                    pcall(function()
                        RunFunction(GiveOwnGlobals(Func, {script = Script}))
                    end)
                end
            end
            for Index, Value in next, Xml do
                if type(Value) == "table" then
                    RunFunction(Value.Function, Value.Script)
                end
            end
        end
        LoadScripts(Obj)
    end
    load(Dex)
end

loadDex()
