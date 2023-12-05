print('---------------------------------------------------------------------------')

def random_char(char_num):
    return ''.join((random.choice(string.ascii_letters) for _ in range(char_num)))


url = 'https://spclient.wg.spotify.com/signup/public/v1/account'
headers = {'authority':'spclient.wg.spotify.com', 
 'sec-ch-ua':'"Google Chrome";v="95", " Not;A Brand";v="99", "Chromium";v="95"', 
 'sec-ch-ua-mobile':'Mozilla/5.0 (Linux; Android 11.0.0; SAMSUNG-SM-G991/KSU3CRJ1 Build/R16NW) AppleWebKit/537.36 (KHTML, like Gecko) SamsungBrowser/15.0.2.47 Chrome/94.0.4606.71 Mobile Safari/537.36', 
 'user-agent':'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/95.0.4638.17 Safari/537.36', 
 'sec-ch-ua-platform':'"Windows"', 
 'content-type':'application/x-www-form-urlencoded', 
 'accept':'*/*', 
 'origin':'https://www.spotify.com', 
 'sec-fetch-site':'same-site', 
 'sec-fetch-mode':'cors', 
 'sec-fetch-dest':'empty', 
 'referer':'https://www.spotify.com/', 
 'accept-language':'ko-KR,en;q=0.9'}

def mainfunction():
    while True:
        number = 0
        Email = random_char(14) + '@' + random_char(5) + '.com'
        password = random_char(2) + '35_' + random_char(4) + '16_4' + random_char(3) + '4_' + random_char(2) + '_85' + random_char(2)
        payload = f"birth_day=26&birth_month=04&birth_year=1997&collect_personal_info=undefined&creation_flow=&creation_point=https%3A%2F%2Fwww.spotify.com%2Fus%2F&displayname=image&gender=male&iagree=1&key=a1e486e2729f46d6bb368d6b2bcda326&platform=www&referrer=&send-email=0&thirdpartyemail=1&email={Email}&password={password}&password_repeat={password}"
        response = requests.request('POST', url, headers=headers, data=payload)
        print(Email + ':' + password)
        files = open('계정.cfg', 'a')
        files.write(Email + ':' + password + '\n')
        files.close


if __name__ == '__main__':
    mainfunction()
