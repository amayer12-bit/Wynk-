# Wynk-
Application de communication
// App.js
import React from 'react';
import { StyleSheet, Text, View, Button, Image, TextInput, ScrollView, TouchableOpacity } from 'react-native';

const App = () => {
  const [username, setUsername] = React.useState('');
  const [posts, setPosts] = React.useState([
    {
      id: 1,
      image: 'https://example.com/image1.jpg', // Remplacez ceci par le lien de l'image
      caption: 'Une belle photo de la nature',
      likes: 0,
    },
    {
      id: 2,
      image: 'https://example.com/image2.jpg', // Remplacez ceci par le lien de l'image
      caption: 'Un moment incroyable!',
      likes: 0,
    },
  ]);

  const handleLogin = () => {
    alert(Bienvenue, ${username});
  };

  const likePost = (id) => {
    setPosts(posts.map(post => {
      if (post.id === id) {
        return { ...post, likes: post.likes + 1 };
      }
      return post;
    }));
  };

  return (
    <ScrollView style={styles.container}>
      <View style={styles.loginContainer}>
        <Text style={styles.title}>Connexion</Text>
        <TextInput
          style={styles.input}
          placeholder="Nom d'utilisateur"
          value={username}
          onChangeText={setUsername}
        />
        <Button title="Se connecter" onPress={handleLogin} />
      </View>
      <View style={styles.postsContainer}>
        <Text style={styles.homeTitle}>Publications</Text>
        {posts.map(post => (
          <View key={post.id} style={styles.post}>
            <Image source={{ uri: post.image }} style={styles.image} />
            <Text>{post.caption}</Text>
            <TouchableOpacity onPress={() => likePost(post.id)}>
              <Text style={styles.likeButton}>👍 {post.likes} J'aime</Text>
            </TouchableOpacity>
          </View>
        ))}
      </View>
    </ScrollView>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
    padding: 20,
    backgroundColor: '#f5f5f5',
  },
  loginContainer: {
    marginBottom: 30,
  },
  title: {
    fontSize: 24,
    marginBottom: 20,
    fontWeight: 'bold',
  },
  input: {
    height: 40,
    borderColor: 'gray',
    borderWidth: 1,
    width: '100%',
    paddingHorizontal: 10,
    marginBottom: 20,
  },
  postsContainer: {
    marginTop: 20,
  },
  homeTitle: {
    fontSize: 20,
    marginBottom: 10,
    fontWeight: 'bold',
  },
  post: {
    marginBottom: 20,
  },
  image: {
    width: '100%',
    height: 200,
  },
  likeButton: {
    marginTop: 10,
    fontSize: 16,
    color: 'blue',
  },
});

export default App;
