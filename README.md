# hw1232312

Сайт: https://calcus.ru/kalkulyator-rashoda-topliva 

*** Settings ***
Library           SeleniumLibrary
Library           OperatingSystem

*** Variables ***
${BROWSER}        Chrome
${URL}            https://www.calculator.net/fuel-consumption-calculator.html
${distance}       100
${price_per_liter} 45

*** Test Cases ***
Calculate Fuel Consumption
    Open Browser    ${URL}    ${BROWSER}
    [Documentation]    Calculate fuel consumption using the fuel consumption calculator
    Select From List By Value    id=uscal    metric
    Input Text    id=currDist    ${distance}
    Input Text    id=currFuel    10
    Input Text    id=fuelPrice    ${price_per_liter}
    Click Element    id=calcost
    Wait Until Element Is Visible    id=litresNeeded
    ${liters}    Get Text    id=litresNeeded
    ${total_cost}    Get Text    id=fuelCost
    Log    Total Liters Needed: ${liters}
    Log    Total Cost: ${total_cost}
    Capture Page Screenshot
    Close Browser
