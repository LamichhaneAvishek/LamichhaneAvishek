
import asyncio
from pyppeteer import launch

async def create_profile():
    browser = await launch(headless=False)  # Launch Chrome
    page = await browser.newPage()  # Create a new page
    await page.goto('chrome://settings/people')  # Go to Chrome's profile management page
    await page.waitForSelector('.add-person-button')  # Wait for the add person button to load
    await page.click('.add-person-button')  # Click on the add person button
    await page.waitForSelector('.md-input[name="name"]')  # Wait for the name input field to load
    await page.type('.md-input[name="Avishek"]', 'Avishek')  # Type your name into the input field
    await page.click('.add-person-button')  # Click on the add person button to create the profile
    await browser.close()  # Close the browser

asyncio.get_event_loop().run_until_complete(create_profile())  # Run the function