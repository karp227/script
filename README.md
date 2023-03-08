state = {
name = "", — Name of the state
population = 0, — Population of the state
capital = {
name = "", — Name of the capital
population = 0 — Population of the city
},
cities = {},
towns = {}
}

— Create a new state from the structure
function state:new(name, population, capitalName, capitalPopulation)
local s = {}
setmetatable(s, self)
self.__index = self

s.name = name
s.population = population

s.capital.name = capitalName
s.capital.population = capitalPopulation

return s
end

— Add cities and towns to the state
function state:addCity(name, population)
local c = {name = name, population = population}
table.insert(self.cities, c)
end

function state:addTown(name, population)
local t = {name = name, population = population}
table.insert(self.towns, t)
end

— Create states
texas = state:new("Texas", 25674681, "Austin", 820484)
colorado = state:new("Colorado", 5029196, "Denver", 649495)

— Add cities and towns to each of the states
texas:addCity("Houston", 2145000)
texas:addCity("San Antonio", 1409019)
texas:addTown("El Paso", 680976)

colorado:addCity("Denver", 649495)
colorado:addTown("Colorado Springs", 451464)
colorado:addTown("Aurora", 391935)

— Print information about the states
print("State: " .. texas.name .. ", Population: " .. texas.population)
print("Capital: " .. texas.capital.name .. ", Population: " .. texas.capital.population)
for _, city in ipairs(texas.cities) do
print(city.name .. ", Population: " .. city.population)
end
for _, town in ipairs(texas.towns) do
print(town.name .. ", Population: " .. town.population)
end

print("State: " .. colorado.name .. ", Population: " .. colorado.population)
print("Capital: " .. colorado.capital.name .. ", Population: " .. colorado.capital.population)
for _, city in ipairs(colorado.cities) do
print(city.name .. ", Population: " .. city.population)
end
for _, town in ipairs(colorado.towns) do
print(town.name .. ", Population: " .. town.population)
