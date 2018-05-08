Merge the meeting times if they overlap with startTime or endTime

```Javascript
function mergeRanges(meetings) {
    let sortedMeetings = meetings.sort((prev, curr) => prev.startTime > curr.startTime);
    let mergedMeetings = [sortedMeetings[0]];

    for (let i = 0; i < sortedMeetings.length; i++) {
        let currentMeeting = sortedMeetings[i];
        let prevMergedMeeting = mergedMeetings[mergedMeetings.length - 1];

        if (currentMeeting.startTime <= prevMergedMeeting.endTime) {
            prevMergedMeeting.endTime = Math.max(currentMeeting.endTime, prevMergedMeeting.endTime)
        } else {
            mergedMeetings.push(currentMeeting);
        }
    }
    return mergedMeetings
}

console.log(mergeRanges([
  {startTime: 5, endTime: 8},
  {startTime: 1, endTime: 4},
  {startTime: 6, endTime: 8},
])); // [{startTime: 1, endTime: 4}, {startTime: 5, endTime: 8}];

console.log(mergeRanges([
  { startTime: 0,  endTime: 1 },
  { startTime: 3,  endTime: 5 },
  { startTime: 4,  endTime: 8 },
  { startTime: 10, endTime: 12 },
  { startTime: 9,  endTime: 10 },
])); //   [{ startTime: 0, endTime: 1 }, { startTime: 3, endTime: 8 },{ startTime: 9, endTime: 12 }];

console.log(mergeRanges([
  { startTime: 0, endTime: 1 },
  { startTime: 3, endTime: 5 },
  { startTime: 4, endTime: 8 },
  { startTime: 10, endTime: 12 },
  { startTime: 9, endTime: 10 },
])); // [{ startTime: 0, endTime: 1 },{ startTime: 3, endTime: 8 },{ startTime: 9, endTime: 12 }];
```