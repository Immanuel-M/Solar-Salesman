#include<iostream>
#include <vector>
using namespace std;

//function Prototypes go here
void menuSelection(int &);
void addEdge(vector<int> adj[], int u, int v);
void printGraph(vector<int> adj[], int V);
void printGraph_ShortestPath(vector<int> adj[], int V);

//Build out below for Class and Struct:

// Custom Data structure to store Adjacency list nodes
struct Node {
	int val, cost;
	Node* next;
};

// Custom Data structure to store graph edges
struct Edge 
{
	int src, dest, weight;
};

//Introduce Class:
class Graph
{
	// Function to allocate new node of Adjacency List
	Node* getAdjListNode(int value, int weight, Node* head)
	{
		Node* newNode = new Node;
		newNode->val = value;
		newNode->cost = weight;

		// point new node to current head
		newNode->next = head;

		return newNode;
	}

	int N;  // number of nodes in the graph

public:

	// An array of pointers to Node to represent
	// adjacency list
	Node** head;

	// Constructor
	Graph(Edge edges[], int n, int N)
	{
		// allocate memory
		head = new Node * [N]();
		this->N = N;

		// initialize head pointer for all vertices
		for (int i = 0; i < N; ++i)
			head[i] = nullptr;

		// add edges to the directed graph
		for (unsigned i = 0; i < n; i++)
		{
			int src = edges[i].src;
			int dest = edges[i].dest;
			int weight = edges[i].weight;

			// insert in the beginning
			Node* newNode = getAdjListNode(dest, weight, head[src]);

			// point head pointer to new node
			head[src] = newNode;

		}
	}

	// Destructor
	~Graph() {
		for (int i = 0; i < N; i++)
			delete[] head[i];

		delete[] head;
	}
};

//For Choice 2:
// print all neighboring vertices of given vertex
//This list is for the Travel Route 
//(note the TR in the name)
void printListTR(Node* ptr)
{
	while (ptr != nullptr)
	{
		cout << "->" << ptr->val << " ";
		ptr = ptr->next;
	}
	cout << endl;
}
//For Choice 3:
// print all neighboring vertices of given vertex
void printList(Node* ptr, int i)
{
	while (ptr != nullptr)
	{
		cout << "(" << i << ", " << ptr->val
			<< ", " << ptr->cost << " miles)";

		ptr = ptr->next;
	}

	cout << endl;
}
//Choice 1 & 4 feed off of the Graph class
//********************
//Main Function Here *
//********************
int main()
{
	//Set up base variable
	int UserChoice;

	//Call menuSelection that
	//allows userto choose their option
	menuSelection(UserChoice);
	
	//End compiling
	system("pause");
	return 0;
}
//Guide to Function Prototypes up top(above main):
//*******************
//adjacenty list	*
//*******************
void addEdge(vector<int> adj[], int u, int v)
{
	adj[u].push_back(v);
	adj[v].push_back(u);
}
//**************************************
//Function to print adjaceny list	   *
//This is also a graph representation  *
//**************************************
void printGraph(vector<int> adj[], int V)
{
	for (int v = 0; v < V; ++v)
	{
		cout << "\nCity: " << v << "\nAdjacent to:";
		for (auto x : adj[v])
			cout << "->" << x ;
		printf("\n");
	}
}
//**************************************
//Function to to print shortest path   *
//This is also a graph representation  *
//**************************************
void printGraph_ShortestPath(vector<int> adj[], int V)
{
	for (int v = 0; v < V; ++v)
	{
		cout << "\nCity: " << v << "\nShortest path:";
		for (auto x : adj[v])
			cout << "->" << x ;
		printf("\n");
	}
}
//************************
//Menu Selection For User*
//************************
void menuSelection(int &choice)
{
	do
	{
		//Display this menu selection to user.
		cout << "-----------------------\n";
		cout << "Welcome to Solar Sales!";
		cout << "\n-----------------------\n";
		cout << "Please select an option from the menu below:\n";
		cout << "1. Travel Route Options\n";
		cout << "2. Field Map (Matrix)\n";
		cout << "3. Adjacent City Path\n";
		cout << "4. Shortest trip\n";
		cout << "5. Exit program\n";
		cout << "\nchoice: ";

		//User input to select choice
		cin >> choice;
		
		//Force User to pick correct range.
		while (choice < 0 || choice > 5)
		{
			//housekeeping for the program
			cout << "That is not a valid option,\n"
				<< "please pick a selection between 1 - 5\n";
			
			//User chooses again
			cin >> choice;
		}
		if (choice == 1)
		{
			//List possible travel routes
			//Display City (for reference to user)
			cout << "Travel Routes:\nCity 0 (Riverside), City 1 (Moreno Valley), "
				<< "City 2 (Perris), City 3 (Hemet)" << endl;
			cout << "---------------------------------------"
				<< "------------------------------------\n";

			// array of graph edges as per above diagram.
			Edge edges[] =
			{
				// pair (x, y) represents edge from x to y
				{ 0, 1 }, { 0, 2 }, { 0, 3 }, { 1, 2 },
				{ 1, 3 }, {1, 0}, { 2, 3 }, { 2, 1}, {2, 0},
				{ 3, 0}, {3,1}, {3,2}
			};

			//Local Variable for Number of vertices in the graph
			int N = 4;

			// calculate number of edges
			int n = sizeof(edges) / sizeof(edges[0]);

			// construct graph
			Graph graph(edges, n, N);

			// print adjacency list representation of graph
			for (int i = 0; i < N; i++)
			{
				// print given vertex
				cout << i << " --";

				// print all its neighboring vertices
				printListTR(graph.head[i]);
			}
			//2 new lines
			cout << "\n\n";
		}
		else if (choice == 2)
		{
			//(Field Map)

			//Display City (for reference to user)
			cout << "City 0 (Riverside), City 1 (Moreno Valley), "
				<< "City 2 (Perris), City 3 (Hemet)" << endl;
			cout << "---------------------------------------"
				<< "------------------------------------\n";

			// array of graph edges as per above diagram.
			Edge edges[] =
			{
				// (x, y, w) -> edge from x to y having weight w
				{ 0, 1, 16 }, { 0, 2, 24 }, { 0, 3, 33 }, { 1, 2, 18 },
				{ 1, 3, 26 }, { 2, 3, 30 }
			};

			// Local Variable for Number of vertices in the graph
			int N = 4;

			// calculate number of edges
			int n = sizeof(edges) / sizeof(edges[0]);

			// construct graph
			Graph graph(edges, n, N);

			// print adjacency list representation of graph
			for (int i = 0; i < N; i++)
			{
				// print all neighboring vertices of vertex i
				printList(graph.head[i], i);
			}
			//2 new lines
			cout << "\n\n";
		}
		else if (choice == 3)
		{
			//Local Variable for number of Cities (Verticies)
			int V = 4;

			//allocate new memmory for vector array
			vector<int>* adj = new vector<int>[V];
			
			//Display City (for reference to user)
			cout << "City 0 (Riverside), City 1 (Moreno Valley), "
				<< "City 2 (Perris), City 3 (Hemet)" << endl;
			cout << "---------------------------------------"
				<< "------------------------------------";
				
			//Output adjacency list.
			addEdge(adj, 0, 1);
			addEdge(adj, 0, 2);
			addEdge(adj, 0, 3);
			addEdge(adj, 1, 2);
			addEdge(adj, 1, 3);
			addEdge(adj, 2, 3);

			//print out the graph
			printGraph(adj, V);
			
			//2 new lines
			cout << "\n\n";

			//desconstruct memmory allocation
			delete[] adj;
		}
		else if (choice == 4)
		{
			//Possible Short Paths
			//Local Variable for number of Cities (Verticies)
			int V = 4;

			//allocate new memmory for vector array
			vector<int>* adj = new vector<int>[V];

			//Display City (for reference to user)
			cout << "Starting from City 0 (Riverside):\n";
			cout << "City 1 (Moreno Valley-16 miles), City 2 (Perris-24 miles),"
				<< " City 3 (Hemet-33 miles)" << endl;
			cout << "---------------------------------------"
				<< "-------------------------------------------";

			//Output adjacency list from starting point.
			addEdge(adj, 0, 1);
			addEdge(adj, 0, 2);
			addEdge(adj, 0, 3);
			
			//print out the graph
			printGraph_ShortestPath(adj, V);
			
			//2 new lines
			cout << "\n\n";

			//desconstruct memmory 
			delete[] adj;
		}
		else
			//Display default message
			cout << "\nThanks for using this program."
			<< " See you next time!\n";
			
	} while (choice != 5);
	
	
}
