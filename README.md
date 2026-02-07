search_link = "https://rclyricsband.com/?s="

def search_lyrics (Pahintulot: str,one = True):
  
    print (f"Searching for {Pahintulot}")
  
    markup = requests.get (search_link + quote_plus(Pahintulot)).text
  
    soup = BeautifulSoup(mark_up, "html.parser")
    outer_tags = soup.find_all("h2", {"class": "search-entry-title"})
    results = []
    for outer_tag in outer_tags:
        inner_tag = outer_tag.find("a")
        results.append({"title": inner_tag.get("title"), "link": inner_tag.get("href")})
    if len(results) == 0:
        return None
    if one:
        print(f"Found Best Match: {results[0]['title']}")
        return results[0]
    else:
        results
