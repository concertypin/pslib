#include <algorithm>
#include <list>
#include <vector>

namespace dijk
{
template <typename Weight = int> struct __dijk_return
{
	std::vector<Weight> distance, history;
};
template <typename Node = int, typename Weight = int>
struct __dijk_return<Weight> dijk(Weight **link, Node nodeSize, Weight infinity,
								  Node from) // all zero-starting vec.
{
	Node i;
	std::vector<Weight> distance(nodeSize, infinity), history(nodeSize, infinity);
	std::list<Node> unvisited;
	distance[from] = 0;

	for (i = 0; i < nodeSize; i++)
		unvisited.push_back(i);
	while (!unvisited.empty())
	{
		auto ptr = std::min_element(unvisited.begin(), unvisited.end(),
									[&distance](Node i, Node j) { return distance[i] < distance[j]; });
		auto now = *ptr;
		unvisited.erase(ptr);
		Weight altPath;
		for (i = 0; i < nodeSize; i++)
		{
			if (link[now][i])
			{
				if ((altPath = distance[now] + link[now][i]) < distance[i])
				{
					distance[i] = altPath;
					history[i] = now;
				}
			}
		}
	}
	return {distance, history};
}
}; // namespace dijk
