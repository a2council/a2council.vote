# a2council voting charts

Welcome to the a2council voting charts project! To see it in action, go to [a2council.vote](https://a2council.vote).

## Creating a chart

1. Start a new branch off of `main`.
1. Copy the most recent meeting folder (it's easier than starting from scratch).
1. Modify the copy to be appropriate for the meeting: Update dates, look at the agenda and see if there's anything that is likely to be interesting or provoke discussion, clear out the csv. Important: adjust the dates in the yaml front matter to be correct for the meeting.
1. Push the branch and check the temporary url to make sure it looks good. You can also run it locally with `hugo serve -D -F`.

Advice: merge this to main once the meeting preview is reasonable, so that we have a url we can tweet out with a brief description of the meeting.

## Using a2councilbot tools to dump a chart

Advice: Do this a few times during the meeting to see if everything is reasonable. You can create a separate branch and update it a few times, looking at the preview url as you go. Once the meeting is over, you can merge to main. It's much easer to keep up during the meeting than to go back and figure stuff out afterwards.

1. get `a2councilbot` from this org and check it out locally.
1. Determine the ID of the meeting:
    ```
    ❯ python3 find_events.py 2022-09-06
    11706 2022-09-06T00:00:00 7:00 PM Downtown Area Citizens Advisory Council (CAC)
    11756 2022-09-06T00:00:00 7:00 PM City Council
    12137 2022-09-06T00:00:00 3:00 PM Employees' Retirement System Board of Trustees
    ```
1. Dump the meeting's data:
    ```
    ❯ python3 make_csv.py --event-id 11756 > ../a2council.vote/content/post/council-meeting-2022-09-06/chart.csv
    2022-09-05 14:59:52,933 - INFO - Starting new polling run...
    2022-09-05 14:59:52,959 - DEBUG - Starting new HTTPS connection (1): webapi.legistar.com:443
    2022-09-05 14:59:53,657 - DEBUG - https://webapi.legistar.com:443 "GET /v1/a2gov/events/11756 HTTP/1.1" 200 1158
    2022-09-05 14:59:53,686 - DEBUG - Starting new HTTPS connection (1): a2gov.legistar.com:443
    2022-09-05 14:59:53,943 - DEBUG - https://a2gov.legistar.com:443 "GET /MeetingDetail.aspx?LEGID=11756&GID=55&G=505481FE-B2ED-4B34-9A92-FDB26536D1E1 HTTP/1.1" 200 None
    ...
    2022-09-05 15:00:07,808 - INFO - Polling run complete
    ```
1. Check out the csv it generated and make sure it's reasonable. It's probably not perfect on the first pass, especially if there are strange parliamentary shenanigans that occur.
