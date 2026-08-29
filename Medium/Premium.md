Premium

### Python
```
class Solution:
    def findSmallestRegion(self, regions: List[List[str]], region1: str, region2: str) -> str:
        def dfs(node):
            if graph[node]:
                visited.add(graph[node])
                dfs(graph[node])

        def dfs2(node):
            return node if node in visited else dfs2(graph[node])

        graph = defaultdict(str)
        for region in regions:
            p = region[0]
            for i in range(1, len(region)):
                graph[region[i]] = p
        visited = {region1}
        dfs(region1)
        return dfs2(region2)
```


### Go
```go
func findSmallestRegion(regions [][]string, region1 string, region2 string) string {
    graph := make(map[string]string)
    for _, region := range regions {
        p := region[0]
        for i := 1; i < len(region); i++ {
            graph[region[i]] = p
        }
    }
    visited := make(map[string]bool)
    r := region1
    visited[r] = true
    for graph[r] != "" {
        r = graph[r]
        visited[r] = true
    }
    r = region2
    for !visited[r] {
        r = graph[r]
    }
    return r
}
```


### C#
```c#
public class Solution {
    public string FindSmallestRegion(IList<IList<string>> regions, string region1, string region2) {
        Dictionary<string, string> graph = new();
        foreach (IList<string> region in regions) {
            string p = region[0];
            for (int i = 1; i < region.Count; i++) {
                graph[region[i]] = p;
            }
        }
        HashSet<string> visited = new (){ region1 };
        string r = region1;
        while (graph.TryGetValue(r, out string nextParent)) {
            visited.Add(nextParent);
            r = nextParent;
        }
        r = region2;
        while (!visited.Contains(r)) {
            r = graph[r];
        }
        return r;
    }
}
```