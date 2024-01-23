#include <iostream>
#include <queue>
#include <string>
using namespace std;

struct Music {
  string title;
  string artist;
  int duration;
};

void displayMenu();
void displayPlaylist(queue<Music>);

int main() {

  queue<Music> playlist;

  int choice;

  do {

    displayMenu();

    cout<<"Choose option: ";
    cin>>choice;

    if(choice==1) {
      string title,artist;
      int duration;
      cout<<"Enter song details:"<<endl;
      cout<<"Title: ";
      cin.ignore();
      getline(cin,title);
      cout<<"Artist: ";
      getline(cin,artist);
      cout<<"Duration: ";
      cin>>duration;

      Music song={title,artist,duration};
      playlist.push(song);
    }
    else if(choice==2) {
      displayPlaylist(playlist);
    }

  } while (choice!=3);

  return 0;
}

void displayMenu() {
  cout<<"\nPlaylist Menu By Yosua IHK TI 1B: "<<endl;
  cout<<"1. Add Song"<<endl;
  cout<<"2. Display Playlist"<<endl;
  cout<<"3. Exit"<<endl;
}

void displayPlaylist(queue<Music> playlist) {
  cout << "\nPlaylist Yosua:" << endl;
  while (!playlist.empty()) {
    Music song = playlist.front();
    cout << song.title << " - " << song.artist << " (" << song.duration << "s)" << endl;
    playlist.pop();
  }
  cout << endl;
}
