import requests
from bs4 import BeautifulSoup
import re

def social_links(soup):
    links = []
    for link in soup.find_all('a', href=True):
        if re.search(r'facebook\.com|linkedin\.com|instagram\.com|', link['href']):
            links.append(link['href'])
    return links

def emails(soup):
    pat_email = r'\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Z|a-z]{2,7}\b'
    emails = re.findall(pat_email, str(soup))
    return emails

def contacts(soup):
    pat_contact = r'\+\d{1,3} \d{1,3} \d{3} \d{4}'
    contacts = re.findall(pat_contact, str(soup))
    return contacts

def main():
    url = input("Enter the URL: ")
    response = requests.get(url)
    soup = BeautifulSoup(response.text, 'html.parser')

    social = social_links(soup)
    email = emails(soup)
    contact =contacts(soup)

    print("Social links :")
    for link in social:
        print(link)

    print("Email/s:")
    for email in email:
        print(email)

    print("Contact:")
    for contact in contact:
        print(contact)

if __name__ == "__main__":
    main()
